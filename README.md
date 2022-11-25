# ROKS-React-Hands-On :cloud: 

Para el desarrollo de este proyecto se tiene como base el desarrollo de una aplicación basada en la librería React de javascript y su posterior despliegue en un **Cluster de OpenShift** que se encuentra alojado en **IBM Cloud**.

<br />

### Indice
1. [Despliegue en OpenShift desde IBM Cloud shell](#Despliegue-en-OpenShift-desde-IBM-Cloud-shell-)
2. [Despliegue Aplicación Demo en React](#despliegue-aplicación-demo-en-react-⚛️)
3. [Despliegue Aplicación Feedback App Desde la consola web de OpenShift](#despliegue-aplicación-feedback-app-desde-la-consola-web-de-openshift-📦)
4. [Monitoreo de la aplicación](#monitoreo-de-la-aplicación)
5. [Despliegue de una imagen Docker en un contenedor de Openshift](#Despliegue-de-una-imagen-Docker-en-un-contenedor-de-Openshift-)
6. [Referencias](#Referencias)
<br />

## Despliegue en OpenShift desde IBM Cloud shell: 🚀

### Haga 'login' a IBM Cloud desde la línea de comando

Inicialmente debe acceder al shell de IBM Cloud desde el siguiente link:

```
https://cloud.ibm.com/shell
```
<br />

### Acceda al cluster de Open Shift (ROKS) desplegado en IBM Cloud 📦

1.	Inicie sesión e ingrese desde la CLI de OpenShift al clúster en el que se va a trabajar. Para ingresar al clúster que tengamos aprovisionado en nuestra cuenta de IBM Cloud se deben realizar los siguientes pasos:

    * Ingresar a la plataforma de IBM cloud con sus credenciales de inicio de sesión, lo puede hacer desde el siguiente link:

     ```
     https://cloud.ibm.com/
     ```
     <br />
     
    * Diríjase al resource list. Primero debe dar clic en el navigation menu y luego donde dice Resource list, como se puede ver en la siguiente imagen:

      <p align="center">
      <img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
      </p>
      <br />

    * Diríjase a la sección de clústers y dé clic en el que se desea acceder.
      <br />

    * Dé clic en el botón OpenShift web console.
    
      <br />

### Haga 'login' en el cluster de Open Shift (ROKS) desde la linea de comando 📦

Ahora en la parte superior derecha dé clic sobre el ID del correo con el que ingresamos y luego en la sección que dice Copy Login Command.
<br />

<p align="center">
<img width="144" alt="1" src="https://user-images.githubusercontent.com/60987042/76917049-53479180-6890-11ea-91a1-b2c2c9213729.PNG">
</p>
<br />

Y por último vuelva a la terminal que se estaba utilizando, pegue el comando y presione enter.

<br />

### Cree un nuevo proyecto en OpenShift para desplegar las aplicaciones 📦
1.	Cree un nuevo proyecto en el clúster de la siguiente manera:

   ```
   oc new-project <projectname>
   ```
   
   **Nota:** Para el **projectname** coloque **roks + las iniciales de su nombre y apellido.**
   <br />
   
2.	Acceda al proyecto que acabó de crear de la siguiente manera:

   ```
   oc project <projectname>
   ```   
   <br />

## Despliegue Aplicación Demo en React :atom_symbol:

1.	Desde el Shell de IBM cloud digite el siguiente comando para crear una aplicación de react:

   ```
   npx create-react-app react-web-app
   ```
   
   <br />
   
2.	Dirigirse a esta carpeta con el comando:

   ```
    cd react-web-app
   ```
   
   <br />
   
3.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:

   ```
   npx nodeshift --deploy.port 3000 --expose
   ```
   <br />
   
   El resultado de este comando va a ser una respuesta de este tipo, que nos indica que la aplicación se desplegó correctamente.
   <br />
   
   <br />
<p align="center"><img width="600" src="https://github.com/sofiaponteb/ROKS-React-Hands-On/blob/main/img/react-consola.png"></p>
<br />
   
   <br />

4.	Para poder acceder al la URL de la aplicación y realizar la verificación de la misma ingrese a la consola web de OpenShift, en la vista topology

     <br />
<p align="center"><img width="600" src="https://github.com/sofiaponteb/ROKS-React-Hands-On/blob/main/img/react-web-app.png"></p>
<br />

   Y por último solo faltaría dar clic en el link que lo llevará a la aplicación desplegada.
<br />
   <p align="center"><img width="600" src="https://github.com/sofiaponteb/ROKS-React-Hands-On/blob/main/img/pagina-demo.png"></p>
<br />
   
   De esta forma se daría por terminado el despliegue de la aplicación react en openshift.

   <br />
   
   
## Despliegue Aplicación Feedback App Desde la consola web de OpenShift 📦 

Para realizar el despliegue desde la consola web de OpenShift de una  manera más intuitiva se deben seguir los siguientes pasos:

7. Cree un nuevo proyecto con la siguiente sintaxis **handson-nombreapellido**.

<p align="center">
<img width="749" alt="new-project" src="https://user-images.githubusercontent.com/60987042/93888733-0369dd00-fcae-11ea-9918-80bcfd8bb35c.PNG">
</p>

<br />

8. Ingrese a la sección add y luego debe elegir From Catalog.

<br />
   <p align="center"><img width="600" src="https://github.com/sofiaponteb/ROKS-React-Hands-On/blob/main/img/import-git.png"></p>
<br />

9. Ingrese la URL del repositorio de GitHub que contiene la aplicación a desplegar, si lo desea puede ser la siguiente:

https://github.com/sofiaponteb/feedback-app-openshift


10. Una vez seleccionada, presione ```Show Advanced Options``` y baje hasta ```Show Advanced Routing Options```. En el puerto ingrese el puerto donde se expone la aplicación creada. En el caso de react suele ser el puerto **3000**, a menos que haya sido cambiado en el desarrollo de la aplicación.

<br />
   <p align="center"><img width="600" src="https://github.com/sofiaponteb/ROKS-React-Hands-On/blob/main/img/port.png"></p>
<br />

11. Al final de esta página encontrará una sección de opciones avanzadas en la cual encontrará un link de **Scaling**.

<p align="center">
<img width="747" alt="Scaling" src="https://user-images.githubusercontent.com/60987042/93889169-7ecb8e80-fcae-11ea-8c39-c30e2ac90465.PNG">
</p>

<br />

12. La sección de **Scaling**, nos permitirá configurar el número de replicas si deseamos un auto escalamiento para nuestra aplicación.

<p align="center">
<img width="960" alt="replicas" src="https://user-images.githubusercontent.com/60987042/93889521-e71a7000-fcae-11ea-80ca-515528219c9e.PNG">
</p>

<br />

13. Al dar clic en crear se iniciará un proceso de build el cual nos entregará el link de despliegue de nuestra aplicación".

<br />
   <p align="center"><img width="600" src="https://github.com/sofiaponteb/ROKS-React-Hands-On/blob/main/img/feedback-app.png"></p>
<br />


**Nota:** Espere unos cuantos segundos mientras el proceso de construcción y despliegue de la aplicación se termina.

<br />

14. Una vez terminado el proceso de despliegue puede dirigirse a Routes, donde podrá ver la URL mediante la cual podrá acceder a la aplicación ya desplegada.

<br />
   <p align="center"><img width="600" src="https://github.com/sofiaponteb/ROKS-React-Hands-On/blob/main/img/feedback-url.png"></p>
<br />

<br />

### Monitoreo de la aplicación

Para realizar un monitoreo de la aplicación desplegada debe seguir los pasos que se indican a continuación:

1. Dé click en la pestaña del proyecto (parte superior) y allí busque y seleccione el proyecto ```openshift-monitoring```. Este namespace está creado por defecto y contiene herramientas como Prometheus y Grafana que permiten monitorear el clúster. Observe los componentes que aparecen y dé click en la opción ```Open URL``` que aparece para Grafana.

<p align="center">
<img src="https://github.com/emeloibmco/ROKS-Angular-HandsOn-4.4/blob/master/Grafana_acceso.gif">
</p>
<br />

2. Esta acción nos va a redirigir a una nueva ventana de nuestro navegador en la cual debemos seleccionar nuestro método de acceso al cual debemos dar clic en **Log in with Openshift**.

<p align="center">
<img width="960" alt="log in grafana" src="https://user-images.githubusercontent.com/60987042/93893051-d1a74500-fcb2-11ea-8982-24db221aec48.PNG">
</p>
<br />

3. En esta nueva ventana inicialmente nos aparecerá un mensaje de autorización en cual debemos dar clic en **Allow Selected Permissions**.

<p align="center">
<img width="960" alt="acces" src="https://user-images.githubusercontent.com/60987042/93896923-1fbe4780-fcb7-11ea-9a69-dc23dd35f814.PNG">
</p>
<br />

4. Al completar el paso anterior nos aparecerá el Dashboard inicial de Grafana, la cual es la herramineta de monitoreo que viene integrada con openshift.

<p align="center">
<img width="959" alt="grafa" src="https://user-images.githubusercontent.com/60987042/93893080-dbc94380-fcb2-11ea-9733-5e8a37e31d84.PNG">
</p>
<br />

5. Para poder monitorear nuestra aplicacion debemos dar clic en **Home** y acá se nos mostrará un menú desplegable en el cual debemos seleccionar lo siguienete:

<p align="center">
<img width="752" alt="menu-grafa" src="https://user-images.githubusercontent.com/60987042/93893179-f69bb800-fcb2-11ea-8263-5f1e8fef79ea.PNG">
</p>
<br />

6. El paso final es en el apartado de **namespace**, buscar nuestro proyecto el cual tenía la syntaxis de **handson-nombreapellido**.

<p align="center">
<img width="960" alt="cpu" src="https://user-images.githubusercontent.com/60987042/93893355-2945b080-fcb3-11ea-99ca-fa8d27a58a97.PNG">
</p>

De esta manera podemos analizar el consumo que se ha tenido en nuestra aplicación tanto en CPU como en Memoria.

<br />

## Despliegue de una imagen Docker en un contenedor de Openshift 📦

Para realizar el despliegue de una aplicación que se encuentra alojada en un una imagen de DockerHub se deben realizar los siguientes pasos:

1. Dé clic en la sección **Add** y luego en la sección ***Container Image*.

<p align="center">
<img width="668" alt="contai" src="https://user-images.githubusercontent.com/60987042/83419932-7e4f7500-a3eb-11ea-8a3a-1a1e2a652adc.PNG">
</p>

<br />

2. Al dar clic en Container Image se abre una ventana en la cual debemos seleccionar el campo **Image Name** y llenar el campo con la ruta fuente de la imagen docker.

<img width="960" alt="librty1" src="https://user-images.githubusercontent.com/45157348/83713481-cd64f800-a5ed-11ea-87b0-420f6f37231f.PNG">
<br />

3. Si reconoce la imagen docker, automaticamente aparece la imagen docker y se llena la información necesaria para el despliegue y se  habilita la opción para dar clic en **CREAR**, y al dar clic acá se inicia el despliegue de la aplicación por lo que se debe esperar un momento mientras se realiza el mismo.

<p align="center">
<img width="501" alt="ibm-sphere" src="https://user-images.githubusercontent.com/45157348/83713491-d35ad900-a5ed-11ea-9f2e-b37163277a29.PNG">
</p>
<br />

4. Una vez terminado el proceso de despliegue puede dirigirse a Overview dando clic sobre el circulo de despliegue, donde podra ver la URL mediante la cual podra acceder a la aplicacion ya desplegada.

<p align="center">
<img width="508" alt="we" src="https://user-images.githubusercontent.com/60987042/83420340-1e0d0300-a3ec-11ea-8d0f-c36e60ff15e7.PNG">
</p>
<br />

5. al dar clic en la URL podrá acceder a la aplicacion ya desplegada.

![image](https://user-images.githubusercontent.com/45157348/83714177-ae676580-a5ef-11ea-8477-841da501564a.png)

<br />

## Referencias

* La documentación en linea de IBM Cloud Red Hat OpenShift Managed, se encuentra en el siguiente enlace: https://cloud.ibm.com/docs/openshift?topic=openshift-getting-started

* En la siguiente página se encuentra la información de administración y configuración de Open Shift 4.11: https://access.redhat.com/documentation/en-us/openshift_container_platform/4.11
<br />

* [Nodeshift](https://nodeshift.dev/)

## Autores ✒️
Equipo *IBM Cloud Tech Sales Colombia*.

