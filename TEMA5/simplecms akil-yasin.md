# Práctica. Instalar CMS basado en XML. GetSimple XML Akil Yassine

### 1.Configuracion inicial

- Instalar Apache2 y PHP
    * Instalacion de Apache2 
        >sudo apt update
        sudo apt install apache2
        sudo ufw app list
        sudo ufw allow 'Apache'
        sudo ufw status
        sudo systemctl status apache2 _**comprobación**_
        sudo mkdir /var/www/html
        sudo nano /etc/apache2/sites-available/html.conf
        - Configuración del archivo **/etc/apache2/sites-available/html.conf**
        ```
        <VirtualHost *:80>
                    ServerAdmin admin@simplecms
                    ServerName simplecms
                    ServerAlias www.simplecms.com
                    DocumentRoot /var/www/html/simplecms
                    ErrorLog ${APACHE_LOG_DIR}/error.log
                    CustomLog ${APACHE_LOG_DIR}/access.log combined
                <Directory "/var/www/html/simplecms">
                    AllowOverride All
                </Directory>
        </VirtualHost>
        ````
        >sudo a2ensite html.conf
        sudo apache2ctl configtest _**comprobamos que el archivo esta correcto**_
        sudo systemctl restart apache2

    * Instalacion de PHP
    >$ sudo apt install php-xml libapache2-mod-php php-curl php-gd php-zip

- Descargar GetSimple
    * Instalar y mover a nuestra carpeta VirtualHost
        + en mi caso la carpeta es : **/etc/var/html/**

* Aplicareos cambios y Daremos los permisios a la Carpeta _**simplecms**_
>
        $ sudo apache2ctl configtest
        $ sudo chown -R www-data:www-data /var/www/html
        $ sudo chmod 755 -R /var/www/html/simplecms
        $ sudo a2enmod rewrite > _**Instalar modulo Mod_Rewrite_**
        $ sudo systemctl restart apache2

### 2.instalacion de GetSimple
1. Accedemos al navegador y en el buscador pondremos nuestra ip/admin.
2. Comprobamos que toda la configuración este bien y iniciamos el setup.  

    + >Si quieres cambiar el idioma al SimpleCMS lo debes hacer ahora si no   lo haces despues es más complicado déspues.
    + >Primero pinchamos en el enlace que nos pone y buscamos el idioma con el que quieras trabajar
en mi caso es es_ES. Pincha aquí para descargar el lenguaje Español
Extraemos el archivo en /var/www/html/simplecms/

3. Acontinuación crearemos usuario y daremos nombre a nuestra pagina

    + En mi caso mi pagina web se llamara Yasin-web
        + Nos saldra una pestaña para entrar en la configuración de nuestra pagina

4. Configuración de nuestra pagina 

    + Activaremos URLs amigables 
    > tendremos que tener ya activado el  modulo Mod_Rewrite 
    + Cambiaeremos Localhost por nuestra ip

5. Modificacion y Creación de las paginas 
    + Iremos a Paginas y nos saldra el index daremos click en sources y modificamos el codigo de la pagina index 
    + En el panel derecho le daremos en crear pagina.
        + Nos saldra la interfaz para crearla e iremos a source 
            + Pondremos el titulo y añadiremos el codigo de la pagina
            + Y por ultimo la añadimos en el menú y le asignamos número de prioridad

        


