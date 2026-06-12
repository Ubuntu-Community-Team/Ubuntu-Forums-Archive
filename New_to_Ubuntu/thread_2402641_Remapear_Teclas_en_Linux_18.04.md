---
title: "Remapear Teclas en Linux 18.04"
date: 2018-10-02
forum: New to Ubuntu
---

### Post by birkoff2 on 2018-10-02
Saludos Comunidad, mi problema es el siguiente, uso linux ubuntu 18.04, pero mi laptop tiene la barra espaciadora mala, y necesito remapear la barra en la tecla control derecho tal como lo tengo con wndows
donde lo realice con un software muy sencillo, alguien me puede orientar, he leido algo sobre el tema, en algunos casos supe que los cambios por consola se desabilitan luego del reinicio y que con autokey se puede hacer pero hay que realizar un script y cargarlo desde el arranque para que efectue el cambio, por favor nuevamente quien me pueda ayudar les estare agradecido.


Pd. teclado en ingles es el de mi laptop

---

### Post by birkoff2 on 2018-10-18
Buenas Noches Comunidad, les cuento que solucione el problema que tenia con la barra espaciadora, gracias a el grupo de Ubuntu  Venezuela a traves de Telegram
la solucion es muy sencilla y la voy a explicar aqui, por si alguien tiene el mismo problema luego
primero que nada deben tener configurado correctamente el teclado, es decir que corresponda el instalado con el que tenga, la pc/laptop
de no ser asi entonces deben identificar el teclado con el comando, en el terminal (ctrl+alt+t) **xmodmap -pke** alli veran que clave esta asignada a cada tecla.
posteriormente con permisos de super usuario, deben ir a la carpeta **usr/share/x11/xkx/symbol** y editar el archivo pc con el comando **sudo gedit pc **
ahi veras las teclas y la accion que ocurre al presionarlas, lo que debes hacer basicamente es copiar lo que esta entre llaves y corchete de la tecla a reasignar y suplantarla
a la tecla nueva es decir ejemplo. si quiero cambiar la barra espaciadora busco la tecla space copio la parte entre llaves y corchetes y me voy a la tecla donde la voy a reasignar ejemplo shift derecho y alli copio lo anterior le damos guardar y salir
para que el cambio sea permanente tenemos que limpiar el cache eso lo realizamos desde el terminal con el siguiente comando 
[B]sudo rm -rf-/var/lib/xkb/*
[/B]reinicias y listo

---

### Post by QIII on 2018-10-18
You have posted in an English-speaking area of the Forums.

While I appreciate that you are sharing the solution you found, your success will be lost on most of the people who visit here.

Please write in English in the English-speaking areas of the Forums, even if your English is rough.  We realize that our members come from all over the world and have a very broad range of cultural experience.

Thanks!

---

