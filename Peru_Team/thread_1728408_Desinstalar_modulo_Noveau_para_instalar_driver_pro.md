---
title: "Desinstalar modulo Noveau para instalar driver propietario nvidia"
date: 2011-04-13
forum: Peru Team
---

### Post by henrysuse on 2011-04-13
quiero instalar el driver privativo de nvidia gtx260m
el que viene incorporado es demasiado lento hasta para mover el mouse pero me sale que debo desinstalar el modulo noveau, hay una opcion para ponerlo en blacklist pero me sale error

[IMG]http://img852.imageshack.us/img852/6868/driveru.jpg[/IMG]

distro: opensuse 10.4 (supongo que es igual linea de comando)

---

### Post by genelyk on 2011-04-17
supóngo q te refieres a la version 11.4 ...  el modulo viene dentro del kernel, eso es un problema x q primero  tienes q ponerle en blacklist, claro entrando como runlevel 3 ,  la verdad es un rollaso desaserce de ese modulo, me demore 3 dias y luego me instale el  driver de nvidia,  sorprsa mia no daba mas de 800x600 de resolucion, loq  hize fue instalar  linuxmint  y me olvide de ese rollo,  claro  no te digo q es la unica opcion si no la  q te kita menos tiempo

---

### Post by solid5 on 2011-06-30
wow la 260m buena laptop =)

matar el noveau es complicado pero no imposible...

primero tiene que "desintalarlo" entre comillas porque igual esta ...

apagar la interfaz grafica de ubuntu median comando en terminal 

bueno lee este post-... y quizas te salga...

[http://ubuntuforums.org/showthread.php?p=10940795#post10940795](http://ubuntuforums.org/showthread.php?p=10940795#post10940795)

en el caso de que aun no puedas, juega con "malograr" el driver reconfigurando el Xserver ,c audno en el grub escoges la opcion de recuperacion de ubuntu...

la idea es q al apagar la interfaz grafica... salga las letras tocas de terminal q es un indicador que el nouveau esta inactivo ....y acon tranquilidad puedes intalar el driver =)

---

