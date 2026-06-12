---
title: "Can't find the package moto4lin to connecto motorola phone"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by miksquik on 2013-03-23
Hi everybody,
I'm trying to connect my motorola cell phone to my computer (ubuntu 12.04). I read that first I have to install moto4lin but I get this when I try it. It basically says that the pakage could not be found (and I don't know what the previous errors mean, but I believe that's to do with something else:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: Tal vez quiera ejecutar «apt-get update» para corregir estos problemas
E: No se ha podido localizar el paquete moto4lin
Can anyone help me out please?
Thanks,
Mik

---

### Post by arpanaut on 2013-03-23
Looks like that program has not been updated since mid 2009, and has no package in the 12.04 repositories.
You might be able to compile from the source package on sourceforge.

I may be wrong but I thought that with most modern phones it was possible to mount and interact with them with the default file browser and related packages.
I know that with my Moto Droid that I can connect with a usb cord and my phones storage cards just appear in the file manager.

---

### Post by drpjkurian on 2013-03-24
I use motorola defy+and I connect my phone via bluetooth to share the files. I've also succeeded in connecting my phone via USB cable or data cable. Never installed any packages for that.

---

### Post by miksquik on 2013-03-24
Thanks for responding...When I connect my phone with the usb cable nothing happens. How can I get the computer to recognise it?

---

### Post by miksquik on 2013-03-24
P.S. I don't have bluetooth on my computer.

---

### Post by ManamiVixen on 2013-03-24
Does your phone has a connection manager built in? Some have one to control USB, like to have differernt modes. Wired Modem mode, Wired File Transfer mode, and No Connection (Charge) Mode are three common types used.

---

### Post by drpjkurian on 2013-03-26
hi
I'm using gingerbread in my motorola defy+. To recognize my phone, I do the following tweakings in my phone.
Go to settings-->Applications-->Development-->and check USB debugging. This procedure will allow your machine to recognize your phone

---

