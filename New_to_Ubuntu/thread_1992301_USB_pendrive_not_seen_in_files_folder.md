---
title: "USB pendrive not seen in files folder"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by giraflorens on 2012-05-31
I just installed ubuntu12.04, and I can not access the pendrive in the USB port in the files folder.  I can reach it with the "disk utility" application, and it appears a one device that works properly, but it is not seen in the files manager.

---

### Post by philinux on 2012-05-31
> **giraflorens said:**
> I just installed ubuntu12.04, and I can not access the pendrive in the USB port in the files folder.  I can reach it with the "disk utility" application, and it appears a one device that works properly, but it is not seen in the files manager.

Plug it in and open a terminal ctrl+alt+t and type in

```
lsusb
```

Post back what it shows.

---

### Post by giraflorens on 2012-05-31
floren@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 13ef:3825  
floren@ubuntu:~$

---

### Post by philinux on 2012-05-31
> **giraflorens said:**
> floren@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**[COLOR="Red"]Bus 001 Device 005: ID 13ef:3825[/COLOR]**  
floren@ubuntu:~$

The system seems to see it [http://usbspeed.nirsoft.net/?pdesc=USB+DISK+2.0+USB+Device&vid=5103&pid=14373](http://usbspeed.nirsoft.net/?pdesc=USB+DISK+2.0+USB+Device&vid=5103&pid=14373)

Is it formatted ok. Post a screenshot from disk utility.

---

### Post by giraflorens on 2012-05-31
Thank a lot for answering.

Screen 1 is from disk manager 
Screen 2 is from file manager (where the USB memory device does not appear)

---

### Post by Mark Phelps on 2012-05-31
Sorry, don't understand the language in the screenshots, but my guess is that Disk Manager is saying the pendrive is unformatted.

To get additional info, please open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out all the partitions and show the filesystem used for each.

---

### Post by philinux on 2012-05-31
> **Mark Phelps said:**
> Sorry, don't understand the language in the screenshots, but my guess is that Disk Manager is saying the pendrive is unformatted.

To get additional info, please open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out all the partitions and show the filesystem used for each.

+1 that's exactly why it is not mounting the drive.

---

### Post by giraflorens on 2012-05-31
Yes it is true.  It is not recognized and can not do any checking of it.  But the Pendrive is formated and well recognized by Windows.  The pendrive format is of type FAT32.  Could that be the reason for Ubuntu not opening it?

---

### Post by philinux on 2012-05-31
> **giraflorens said:**
> Yes it is true.  It is not recognized and can not do any checking of it.  But the Pendrive is formated and well recognized by Windows.  The pendrive format is of type FAT32.  Could that be the reason for Ubuntu not opening it?

Please do what Mark asked in post 6.

---

### Post by giraflorens on 2012-05-31
It is going to be difficult, cause I have the OS in Spanish and all the messages are in Spanish. I will try to translate what it says about the 3rd disk (the external 16GB USB drive)

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x2bd2c32a

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS/exFAT

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador del disco: 0x9274fdc3

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1              63   976768064   488384001   42  SFS

La partición 1 no se inició en el limite físico del sector
The partition 1 was not inizialized in the physical limit of the sector

Disco /dev/sdc: 16.8 GB, 16777216000 bytes
64 cabezas, 32 sectores/pista, 16000 cilindros, 32768000 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x69737369

Esto no parece una tabla de particiones
This seems not being a partitions table

Probablemente ha seleccionado el dispositivo que no era.
Probably you selected the  erroneus device 

device  begin  start end id system
Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   ?  1869771365  2038460886    84344761   69  Desconocido
/dev/sdc2   ?  1701519481  3571400945   934940732+  73  Desconocido
/dev/sdc3   ?        2573        2573           0   74  Desconocido
/dev/sdc4      2885681152  2885733566       26207+   0  Vacía

Las entradas de la tabla de particiones no están en el orden del disco

---

### Post by Mark_in_Hollywood on 2012-05-31
From your Settings / Removable Drives and Media, have a look and tell us what the settings are, please.

---

### Post by giraflorens on 2012-05-31
For all the Removable Drives and Media the option of "Ask what to do" is marked.

I just plug in the PC an External Hard Drive and it conected perfectly (better than with windows).  Migh be the problem with the pendrive is due to the pendrive than to the OS.

---

