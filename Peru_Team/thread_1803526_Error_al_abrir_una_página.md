---
title: "Error al abrir una página"
date: 2011-07-13
forum: Peru Team
---

### Post by eduar2083 on 2011-07-13
Buenos días a todos. Después de casi 3 años he vuelto a usar Ubuntu 8.04 que tengo en la otra partición de mi HD. El asunto es que no tengo problemas para conectarme a internet desde WinXP pero ocurre error de conexión desde Linux. Podrían indicarme si debo hacer alguna configuración talvez. Este problema no me ocurría hace 3 años cuando recién lo instalé.
Muchas gracias por alguna respuesta.

---

### Post by genelyk on 2011-07-13
especifica el tipo de conexion  inalambrico , cableada, estas detras de un router o proxy, q mensaje de error sale, alguna ultima actualizacion instalada............

---

### Post by eduar2083 on 2011-07-14
Gracias **genelyk** por tu respuesta. Disculpa por la poca información que brindé. Utilizo un módem inalámbrico(TP Link). Adjunto 2 caputras de pantalla para que observes los mensajes de error.
[IMG]http://img194.imageshack.us/img194/4072/pantallazozo.png[/IMG]
[IMG]http://img194.imageshack.us/img194/4623/pantallazoerrordecargad.png[/IMG]
Un saludo y gracias.

---

### Post by genelyk on 2011-07-14
mmm  has probado el clic derecho encima del icono de red y darle en activar  eth0 .
q info te muestra cuando en la consola haces   
$ ifconfig eth0

---

### Post by eduar2083 on 2011-07-14
Al darle clic derecho sobre el ìcono de red, me muestra las opciones:
-Activar red (está con check)
-Editar conexiones
-Acerca de
 
Al pinchar en **Editar conexiones** - solapa **Cableada**, me muestra la siguiente pantalla:
[IMG]http://img29.imageshack.us/img29/5267/conexionesdered.png[/IMG]
 
Por otro lado al hacer **ifconfig eth0** en la terminal, me arroja los resultados siguientes:
[IMG]http://img813.imageshack.us/img813/7356/ifconfing.png[/IMG]
Agradezco mucho tu tiempo y espero me puedas ayudar.
Un saludo, gracias.

---

### Post by genelyk on 2011-07-15
mmm no veo nada de  ip local,  q raro, bueno mejor ledas clic en  donde dice eth0  y  luego en editar, y le pones alguna fija manualmente,  192.168.1.123 255.255.255.0 192.168.1.1    pv4 .   algo se me viene a la mente con la red, ase tiempo tuve un problema similar creo  no me acuerdo bien uhmmm

---

### Post by solid5 on 2011-07-15
Tu cable no estara bien.....

mmm prueba el ubuntu desde el cd en modo live, conecta tu red y cheka si funciona...

y avisanos si se puede conectar o no..

---

### Post by Guman on 2011-08-15
ese error es familiar como dice genelyk,
pero en el caso mio fue por k aunk parece mentira  la instalacion no completo en modo perfecto, por la razon k sea....
a pesar de no mostrar errores ni avisos de error a veces pasa eso, sugiero k reinstales desde otro disco y previamente limpies la unidad lectora.

---

### Post by eduar2083 on 2011-08-18
Hola. Agradezco por sus respuestas. No tuve otra opción que reinstalar Linux pero cometí un gravísimo error. Les comento rápidamente lo que me sucedió. Tenía Ubuntu y le había puesto password al grub usando un tuto que encontré hace algunos años en esta web. Había dedicido reinstalarlo para ver si así se solucionaba el mencionado problema y procedí eliminando las 2 particiones(swap - ext3) desde Windows usando Partition Wizard. Al reiniciar el pc mi peor temor acerca del grub se hizo realidad, Windows no cargaba, el grub lanzaba un código de error, lo peor en ese momento es que tenía la lectora averiada. Tuve que conseguirme una para reemplazarla y poder reinstalar Ubuntu, así lo hice. Ahora el grub obviamente aparece sin pass pero el problema es que para iniciar sesión me pide ingresar un usuario y contraseña en 2 cajas de texto. He probado de todo hasta con campos vacíos pero na. Ya no deseo esta versión de Linux, quisiera probar con la más actual, podrían proporcionarme el enlace para poder solicitarla.
Les agradezo mucho.
Un saludo.

---

### Post by genelyk on 2011-08-18
el shipit ya no existe, si quieres bajarlo entonces entra a: 
[http://cdimage.ubuntu.com/releases/11.04/release/](http://cdimage.ubuntu.com/releases/11.04/release/)

---

### Post by eduar2083 on 2011-08-19
Gracias **genelyk**. Voy a descargar y grabarlo en un disco.
Un saludo.

---

