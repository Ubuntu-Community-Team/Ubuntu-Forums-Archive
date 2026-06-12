---
title: "How to clean the system?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by zaurus on 2008-07-26
Hello

I have compiled and installed some modules for my DVB but not happy and want to do it again with the new source. What is the proper way to do that? How to uninstall and clean the system from previous compillation/installation?

Other question
I have many kernel installed on the system after Ubuntu automatic updates. They takes places on my HD. How to remove the kernel I do not need in proper way?

KR

---

### Post by iaculallad on 2008-07-26
> **zaurus said:**
> Hello

Other question
I have many kernel installed on the system after Ubuntu automatic updates. They takes places on my HD. How to remove the kernel I do not need in proper way?

KR

Use the Synaptics Package Manager, use the "linux-image" as search string (w/o quote). Right-click on the OLD kernel file that you want remove and select "Mark for Complete Removal". Do the same process for other OLD kernels you want remove. When finished selecting kernels to be uninstalled, click on the apply button.
This process will automatically update your GRUB boot menu file.

---

### Post by zaurus on 2008-07-26
> **iaculallad said:**
> Use the Synaptics Package Manager, use the "linux-image" as search string (w/o quote). Right-click on the OLD kernel file that you want remove and select "Mark for Complete Removal". Do the same process for other OLD kernels you want remove. When finished selecting kernels to be uninstalled, click on the apply button.
This process will automatically update your GRUB boot menu file.

Thanks for that!
Hope someone help me with the first question also.

KR

---

### Post by zvacet on 2008-07-26
>  How to uninstall and clean the system from previous compillation/installation?

If you used **make install** command when you installed package go to the folder in wich you compile package and type **sudo make uninstall**.If you used **checkinstall **then you can remove package from synaptic.

---

### Post by zaurus on 2008-07-26
> **zvacet said:**
> If you used **make install** command when you installed package go to the folder in wich you compile package and type **sudo make uninstall**.If you used **checkinstall **then you can remove package from synaptic.

Thanks zvacet!
Package I want to remove is DVB drivers loaded when booting the system. They are in use. Should I unload them before using make uninstall? How can I do it?

KR

N.B.
I never heared about checkinstall. Is it something specific for Ubuntu? Can one use it every time instead of make install? Any advantage to use it?

P.S.
I tryed now sudo make uninstall in the folder I did sudo make install. I have the following error so: 
"make -C /home/sacha/mantis-08f27ef99d74/v4l uninstall
make[1]: Entering directory `/home/sacha/mantis-08f27ef99d74/v4l'
make[1]: *** No rule to make target `uninstall'.  Stop.
make[1]: Leaving directory `/home/sacha/mantis-08f27ef99d74/v4l'
make: *** [uninstall] Error 2"

---

