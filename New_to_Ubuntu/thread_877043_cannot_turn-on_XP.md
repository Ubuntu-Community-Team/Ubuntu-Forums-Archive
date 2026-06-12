---
title: "cannot turn-on XP"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by zorton01 on 2008-08-01
Hello everybody,

Ive just installed Ubuntu from the Image CD i downloaded from Ubuntu. Ive firts run it with the CD (trial). after that trial, i decided to install it, directly from the CD. So I choosed the XP Ubuntu dual option. The CD made automatically the partition and installed it. I just had a firts option of choosing the system to start witj, so entered the Ubuntu. Now, everytime i switch on im not able to boot the XP, just offer me the possibility of running Ubuntu. How can i do to choice a main menu on the boot and run XP or Ubuntu? 

many Thanks for the help

Zorton

---

### Post by overdrank on 2008-08-01
> **zorton01 said:**
> Hello everybody,

Ive just installed Ubuntu from the Image CD i downloaded from Ubuntu. Ive firts run it with the CD (trial). after that trial, i decided to install it, directly from the CD. So I choosed the XP Ubuntu dual option. The CD made automatically the partition and installed it. I just had a firts option of choosing the system to start witj, so entered the Ubuntu. Now, everytime i switch on im not able to boot the XP, just offer me the possibility of running Ubuntu. How can i do to choice a main menu on the boot and run XP or Ubuntu? 

many Thanks for the help

Zorton

Hi and welcome, could you use this command in the terminal and post the output here ```
sudo fdisk -l
``` that is a small L. the terminal is located under applications, accessories. This will allow us to verify that the windows partition is still intact. Then you may have to add it to the grub.

---

### Post by zorton01 on 2008-08-01
ok so thats what i had, i think i deleted my xp partition, right?? 

Uso:   fdisk [-b SSZ] [-u] DISCO    Cambia tabla de particiones
       fdisk -l [-b SSZ] [-u] DISCO Lista tabla(s) de particiones
       fdisk -s PARTICIÓN           Obtiene tamaño de particiones en bloques
       fdisk -v                     Obtiene versión de fdisk
El valor de DISCO tiene el formato /dev/hdb o /dev/sda
y el valor de PARTICIÓN tiene el formato /dev/hda7
-u: Obtener Principio y Final en sectores (en lugar de cilindros)
-b 2048: (Para algunas unidades MO) Utilizar sectores de 2048 bytes
zorton@zorton-laptop:~$ fdisk -l
zorton@zorton-laptop:~$ sudo fdisk -l

Disco /dev/sda: 60.0 GB, 60011642880 bytes
255 cabezas, 63 sectores/pista, 7296 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x6bd10901

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extendida
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

---

### Post by overdrank on 2008-08-01
> **zorton01 said:**
> ok so thats what i had, i think i deleted my xp partition, right?? 

Uso:   fdisk [-b SSZ] [-u] DISCO    Cambia tabla de particiones
       fdisk -l [-b SSZ] [-u] DISCO Lista tabla(s) de particiones
       fdisk -s PARTICIÓN           Obtiene tamaño de particiones en bloques
       fdisk -v                     Obtiene versión de fdisk
El valor de DISCO tiene el formato /dev/hdb o /dev/sda
y el valor de PARTICIÓN tiene el formato /dev/hda7
-u: Obtener Principio y Final en sectores (en lugar de cilindros)
-b 2048: (Para algunas unidades MO) Utilizar sectores de 2048 bytes
zorton@zorton-laptop:~$ fdisk -l
zorton@zorton-laptop:~$ sudo fdisk -l

Disco /dev/sda: 60.0 GB, 60011642880 bytes
255 cabezas, 63 sectores/pista, 7296 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x6bd10901

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extendida
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Yea I am afraid so from the look of it. You can always reinstall windows and this link can help
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by zorton01 on 2008-08-01
ok thanks very much, no problem, as i'm just starting with ubuntu, my HD was backup and XP just installed, so this laptop is just for trial. i will follow instructions on that link.

---

