---
title: "Instalar Driver Nvidia actualizado"
date: 2011-06-15
forum: Peru Team
---

### Post by solid5 on 2011-06-15
Saludos Ubunteros:
 Seguir los siguientes pasos para instalar el driver en la tarjeta  Nvidia de manera manual (no por Gestor de paquetes Sinaptic ni Gestor de  actualizaciones). Considerando que el driver de la web de Nvidia es muy  actualizado en comparación al que t proporciona por defecto el  Sinaptic.
 NOTA: Apuntar los pasos en un papel o imprimirlo si es que lo estas leyendo desde la Pc donde vas a instalar el driver.
 # Primero actualizar el Ubuntu totalmente, ya que a veces salen actualizaciones para el tema de video (server X)
# Descargar el driver NVIDIA-Linux-x86_64-256.44.run (versión actual para linux 64 bits) de la web [www.nvidia.com]("http://www.nvidia.com/"),  seleccionando el modelo de tu tarjeta, tipo de linux 32bits o 64 bits  principalmente. (te recomiendo descargarlo en el escritorio para hacerlo  mas accesible)
# Darle click secundario al archivo driver descargado, hacemos click en  propiedades y luego en la pestaña de permisos y ponemos el visto bueno  en " Permitir ejecutar el archivo como un programa "
# abrir un terminal (Aplicaciones/Accesorios/Terminal)
# primero vamos a "matar" la interfaz gráfica para poder instalar el driver, escribir lo siguiente en la terminal:
 $ sudo /etc/init.d/gdm stop
 #esto lo mandara a pantalla negra con letras, para entrar al modo terminal presionar las siguientes teclas: Ctrl + Alt + F1
#ahora estamos en modo terminal hacemos login poniendo el nombre de usuario y contraseña.
#luego nos vamos al escritorio por la terminal:
 $ cd Escritorio
 # y escribimos:
 $ ls
 # vemos los archivos en el escritorio
# el nombre de driver debe estar de color verde si es así Ejecutamos el driver, teclear en terminal:
 $ sudo ./NVIDIA-Linux-x86_64-256.44.run
 -----------------------------------------------------------------------------------------------------------------------------------------------
# caso contrario tecleamos en la terminal:
 $ sudo chmod -R 777 /home/Nombre_de_Usuario/Escritorio/NVIDIA-Linux-x86_64-256.44.run
$ sudo chmod -X /home/Nombre_de_Usuario/Escritorio/NVIDIA-Linux-x86_64-256.44.run
 # y verificamos de nuevo si el driver esta verde:
 $ ls
--------------------------------------------------------------------------------------------------------------------------------------------------
 # se abrirá un menú de driver de Nvidia, seguir los pasos (darle todo  ok y/o aceptar) , después de eso le regresara al modo terminal, para  eso "revivimos" la interfaz gráfica, escribir en terminal:
 $ sudo /etc/init.d/gdm start
 # Esto lo mandara a la pantalla de login , logueate y veras que puede  usar los efectos visuales de normal o extra (en : click secundario en  el escritorio/cambiar fondo de escritorio/efectos visuales ), además de  tener el menú: Nvidia X Server Setting (Sistema/Preferencias).
 PD: En el caso de una actualizacion en el server X u otro paquete  relacionado con las graficas, puede que se malogre el driver de Nvidia  (se manifiesta en el cambio de resolucion y la perdida de efectos de  escritorio), se puede desinstalar el driver (EL INSTALADOR DEL DRIVER ES  A SU VEZ EL DESINSTALADOR, RECOMIENDO GUARDARLO EN ALGUN LUGAR DE LA  PC) y volver a instalar con los pasos ya mencionados.
 para desinstalar:
 $ sudo ./NVIDIA-Linux-x86_64-256.44.run --uninstall
------------------------------------------------------------------------------------------------------------------------------------------------------
IMPORTANTE: (SOBRE DRIVER NOUVEAU)
 SALUDOS UBUNTEROS, ACTUALMENTE LAS ULTIMAS VERSIONES DE UBUNTU NO  DEJA MATAR LA INTERFAZ GRAFICA BIEN POR EL DRIVER NOUVEAU, SE PUEDE DAR  CUENTA CUANDO MANDA AL TERMINAL SE VEN LAS LETRAS PEQUEÑAS Y FINAS  ADEMAS DE NO DEJAR INSTALAR BIEN EL DRIVER DE NVIDIA QUE DESCARGAMOS  DESDE SU WEB... BUSCANDO EN LAS WEBS, ENCONTRE UNA FORMA DE DESISTALAR  EL DRIVER NOUVEAU:
 Desinstalar el driver libre nouveau con:
sudo apt-get remove --purge xserver-xorg-video-nouveau
 Y Añadir nouveau a la Blacklist para que en el arranque del sistema  no se monte y nos deje arrancar luego sin él. Para ello editamos el  archivo con:
sudo gedit /etc/modprobe.d/blacklist.conf
 Añadimos al final del archivo las siguientes lineas:
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
 Guardamos y cerramos el archivo y reiniciamos

---

