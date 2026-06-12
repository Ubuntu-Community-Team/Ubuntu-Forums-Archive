---
title: "problemas con virtualbox y carpetas compatidas"
date: 2010-11-18
forum: Peru Team
---

### Post by Josedark on 2010-11-18
[SIZE=2]Mis estimados colegas  hace algunas días que  ya no puedo entrar a mis carpetas compartidas tengo windows instaLADO EN VIRTUALBOX sistema  ubuntu 10.04 64bits
de un momento a otro me aparece el mensaje parametro  incorrecto al querer entrar a la carpeta compartida de mi ubuntu  en el virtualbox con windows

creaba una nueva carpeta la compartia entonces si funcinaba, ahora ya ni eso
que puede hacer[/SIZE]
ayudaaaaaaaaaaaaaaaa
se agradece los comentarios

---

### Post by oskargicast on 2010-11-18
> **Josedark said:**
> [SIZE=2]Mis estimados colegas  hace algunas días que  ya no puedo entrar a mis carpetas compartidas tengo windows instaLADO EN VIRTUALBOX sistema  ubuntu 10.04 64bits
de un momento a otro me aparece el mensaje parametro  incorrecto al querer entrar a la carpeta compartida de mi ubuntu  en el virtualbox con windows

creaba una nueva carpeta la compartia entonces si funcinaba, ahora ya ni eso
que puede hacer[/SIZE]
ayudaaaaaaaaaaaaaaaa
se agradece los comentarios

Hola, puedes probar con algo como esto, good luck :p:

sudo mount -t vboxsf compartido /home/oscar/compartido/

---

### Post by Josedark on 2010-11-18
> **oskargicast said:**
> Hola, puedes probar con algo como esto, good luck :p:

sudo mount -t vboxsf compartido /home/oscar/compartido/

como lo pongo 
antes de prender el windows o despues

en la consoa
saludos

---

### Post by oskargicast on 2010-11-19
> **Josedark said:**
> como lo pongo 
antes de prender el windows o despues

en la consoa
saludos

En el terminal cuando inicias la virtualizacion en ubuntu. El problema esque tienes que hacerlo cada vez que inicies. Una alternativa es crear una especie de bash, y que arranque coon el sistema, pero primero intenta si funciona el comando, quizas sea otra cosa.

---

### Post by Josedark on 2011-03-07
> **oskargicast said:**
> En el terminal cuando inicias la virtualizacion en ubuntu. El problema esque tienes que hacerlo cada vez que inicies. Una alternativa es crear una especie de bash, y que arranque coon el sistema, pero primero intenta si funciona el comando, quizas sea otra cosa.


al final reinatalle tood de nuevo  sobre el virtual box
saludos

---

