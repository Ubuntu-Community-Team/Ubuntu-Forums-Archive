---
title: "Brother MCF-9180 in Ubuntu 7.10"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by priscus on 2008-05-24
Hi guys,

I am trying to install my Brother MFC 9180 printer because the driver that Gusty uses, MFC 9100 cause my printer to print strange symbols.
I have been researching info about this printer model and I have found very litlle.
At last y found the original Brother drivers to my printer in .deb format and trying to install by doing this:

$ sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
$ sudo ln -s /etc/init.d/cupsys /etc/init.d/lprng
$ sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
$ sudo dpkg -i mfc9180lpr-1.1.2-1.i386.deb

Then I get this error I can not resolve:

Seleccionando el paquete mfc9180lpr previamente no seleccionado.
(Leyendo la base de datos ...  
93229 ficheros y directorios instalados actualmente.)
Desempaquetando mfc9180lpr (de mfc9180lpr-1.1.2-1.i386.deb) ...
Configurando mfc9180lpr (1.1.2-1) ...
/var/lib/dpkg/info/mfc9180lpr.postinst: 4: /etc/init.d/lpd: Permission denied
dpkg: error al procesar mfc9180lpr (--install):
 el subproceso post-installation script devolvió el código de salida de error 126
Se encontraron errores al procesar:
mfc9180lpr

Once in this point Synaptic tell me I must reconfigure the mfc9180lpr driver and crash.

I am able to resolve the Synaptic crahs by editing the /var/lib/dpkg/status but I am still can not set my MFC 9180 printer to print propperly, so I am asking for your help.

Thanks a lot!

---

### Post by plucky on 2008-05-24
Not sure if this will work as I don't have your Brother printer model but for mine I had to use ```
sudo dpkg -i --force-all mfc9180lpr-1.1.2-1.i386.deb
```
as shown in this [thread](http://ubuntuforums.org/showthread.php?t=590793) for Brother printers.

Good Luck

---

### Post by priscus on 2008-05-24
I have tried your suggestions and read the thread you told me, but it still does not work :(

Thanks a lot for your help!

---

