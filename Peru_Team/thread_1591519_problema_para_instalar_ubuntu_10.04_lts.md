---
title: "problema para instalar ubuntu 10.04 lts"
date: 2010-10-09
forum: Peru Team
---

### Post by kike2803 on 2010-10-09
bueno soy nuevo en el ambiente linux y tengo el siguiente problema al instalar el ubuntu 10.04: al seguir todos los pasos de instalacion desde windows (tengo winxp sp3) al iniciar el so ubuntu me sale el siguiente mensaje:
 
Gave up waiting for root device common problems:
- Boot args (cat/proce/cmdlink)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 
- Missing modules (cat/proc/modules; ls/dev)
 
ALERT! /dev/sda1 doe not exist. Dropping to a shell!
 
 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter ´help´for a listof built-in commands
 
(initramfs) _
 
 
He tratado de instalarlo con wubii (que no corre). Bueno tengo que decir q mi pc es:
PIV DE 1.6 y 512 de ram con hd de 40gb
 
grcias por la ayuda

---

### Post by genelyk on 2010-10-09
mejor instalalo nativamente, osea desde el propio cd live pero te aviso que va ser lentoo cuando lo instales el procesador que tienes es lentoo  cundo inicias gnome y va aser mas lento cuando veas algun video de flash ,,,   prueba xubuntu o linuxmint xfce

---

### Post by davidsonxxi on 2010-10-20
Saludos

No acostumbro juntar agua y aceite y debo suponer que estas instalando en una partición Fat32 que corresponde a las versiones de windows 

supongo que estas familiarizado con windows, tons si tu HDD (disco) es de 40GB puedes crear tres particiones de la siguiente forma: 1:para winxp con uno 12GB, una segunda para win (HDD D) de unos 16 GB y deja libre el resto del disco.

como te han indicado con cualquier cd de linux (Desktop o Alternate) arranca tu PC  e instalas Linux en el espacio libre que son aprox son 12GB .

tu instalador creara por defecto la unidad SWAP que utiliza el sistema como memoria de intercambio y el resto de datos en una sola partición, por defecto lo hará en una partición extendida, pero no te preocupes por eso.

aunque desde windows no podrás acceder facilmente a los archivos de Linux, pero desde Linux podrás acceder a tus dos particiones de windows. (montandolas) desde el menu

bye.

suerte.

---

