---
title: "Installing vmware"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by thedude2008 on 2008-08-12
Could anyone tell me the simplest and most effective way to install a virtual machine on my computer which would allow me to run Windows inside my ubuntu-or any other method of having windows and ubuntu on the same pc. I currently have ubuntu gutsy gibbon but there are certain things I can't do on here which would make windows useful to me

Many thanks

---

### Post by Ryadt on 2008-08-12
Type in terminal```
sudo apt-get install virtualbox-ose
``` This will install virtualbox, an alternative to vmware.

---

### Post by L Campbell on 2008-08-12
> **thedude2008 said:**
> Could anyone tell me the simplest and most effective way to install a virtual machine on my computer which would allow me to run Windows inside my ubuntu-or any other method of having windows and ubuntu on the same pc. I currently have ubuntu gutsy gibbon but there are certain things I can't do on here which would make windows useful to me

Many thanks

I used this:-

[http://wubi-installer.org/](http://wubi-installer.org/)

to install Hardy 8.04 on my PC with XP.

FWIW, it worked absolutely faultlessly for me and, trust me, I am a REAL dunce at computer stuff.

---

### Post by thedude2008 on 2008-08-12
Many thanks for those replies-both very useful. One further question re virtual box. Once it is installed how do I then put Windows into the box and onto my machine

---

### Post by Ryadt on 2008-08-12
Have a look at this tutorial [http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

---

### Post by bodhi.zazen on 2008-08-12
For VMWare see this thread (it is a sticky)

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934") 

wubi is NOT virtualization, it is a variation of dual booting.

If you go with Virtualbox I would advise the edition from the Sun Site :

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by thedude2008 on 2008-08-12
Got this message when trying to install virtual box

FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

Next step?

Cheers

---

### Post by thedude2008 on 2008-08-12
Haven't done anythign but now got this message in terminal

Setting up virtualbox-ose (1.5.0-dfsg2-1ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

What does it all mean?

---

### Post by bawilson2 on 2008-08-12
Here's the guide that I followed to setup windows as a virtual machine.  Worked pretty quickly.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

