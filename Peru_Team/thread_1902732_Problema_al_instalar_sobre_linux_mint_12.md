---
title: "Problema al instalar sobre linux mint 12"
date: 2011-12-31
forum: Peru Team
---

### Post by maximo132 on 2011-12-31
Hola acabo de instalar ubuntu sobre linux mint 12 haciendo que formateara la partición sobre la que se alojaba el anterior sistema pero resulta que ahora las ventanas y los menus presentan la fea apariencia que tiene mint 12 y sólo el dash conserva la apariencia de unity, no se a que se debe pero la barra superior tiene la apariencia anterior, las cabeceras de todas las aplicaciones igual, incluso los menús del click derecho, además hay varios espacios en blanco en la barra de la izquierda que corresponden a aplicaciones que no se muestran pero que al hacerle click levantan.

No se si alguien puede ayudarme a corregir esto pues en realidad creo que en lugar de formatear todo y realizar una instalación limpia sólo se ha fusionado perdiendo todo lo bueno que unity podía ofrecer visualmente.

---

### Post by genelyk on 2012-01-06
intenta cambiando el tema de linuxmint, a mi me paso pero de ubuntu en ubuntu, algunos iconos no salias y era medio extraño, cambie el tema y se soluciono, o en todo caso cambia el nombre de la carpeta .config  q esta en tu /home   si empeora regresa su nombre  la carpeta .config

---

### Post by cintiaarosales on 2012-05-23
Saludos a todos,
@maximo132, probablemente esté en lo cierto en hacer una instalación limpia. Pero si no quiere la molestia de volver a instalar todo hay algunas soluciones que podría intentar, tal vez alguna le funcione. Puede modificar los sistemas de archivos, si se siente cómodo para hacerlo, o utilizar la herramienta de Ubuntu Tweak.
Yo personalmente hice lo siguiente para cambiar el aspecto del fondo de la pantalla de inicio de sesión:
Abrir “unity-greeter.conf” como “root” y ejecutar “gksu gedit/etc/lightdm/unity-greeter.config”.
Localizar la cadena “background=/usr/share/background.jpg”,  luego sustituir esta cadena con la ruta a la imagen deseada (ejemplo: background=/home/Cintia/My Pictures/backgroundIMG.jpg).
Asegúrese de que la opción de solo lectura esta seleccionada para la imagen de fondo que eligió en Permisos de acceso>otros.
También se puede cambiar los temas de Windows, Shell Gnome y de los iconos. Solo debe descargar el tema, descomprimirlo, y abrir la carpeta descomprimida como Administrador. Ahora finalice de establecer la configuración avanzada adecuadamente. :)
Cintia

---

