---
title: "Dell Inspiron 6400"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by fleawhale on 2014-09-23
Hi there, I am installing Ubuntu for the first time and want to check that I am downloading the right thing. I have a Dell Inspiron 6400.
[http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_6400.2FE1505](http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_6400.2FE1505)
Is the 32-bit version that I can download from ubuntu.com the best one to go for for this laptop model? And does it come already with all the drivers for wireless-LAN, mousepad, audiocard etc... or may I have to download drivers separately?
-fleawhale

---

### Post by Mike_Walsh on 2014-09-23
Hello, & welcome to the forums.

You need to find out whether you have a 32- or 64-bit CPU, really. The 32-bit version will run on ANY computer; but if you can run the 64-bit version, you'll get better response from it. According to your specs, your model was offered with either 32- OR 64-bit CPU's; do you know which one you've got?

Dell were notorious for changing hardware specs at the drop of a hat....they were constantly experimenting (not always to good effect,neither).

As for drivers.....don't even worry about that. Most drivers for nearly ALL hardware on the market are installed in the Linux kernel by default; the biggest part of the kernel is nothing BUT drivers. The only one you MIGHT need to hunt down and install will be your graphics card; lots of advice on here for THAT. And if you DO have a problem with other drivers after installing, this is the best place to come to for help......some very knowledgeable folk on here.

Regards,

Mike.

---

### Post by kira-yamato-2008 on 2014-09-23
Depends on your specific processor, and how much system memory you have. So here's a list of things to consider: 

First: Instead of Ubuntu (Which uses the unity desktop which can be a bit demanding.) Try Xubuntu or Lubuntiu, as either Distro is better for lower ram and processors and will result in faster sperds.
 
Second: If you have the Nvidia GeForce 8400M GS GPU don't use Nvidia Binary drivers. There is an issue somewhere and 8000 series GeForce cards are basically universally reported to cause any Linux distribution to lock-up. It's wide spread and seems to affect the 8200, 8300, and 8400 graphics cards with out fail. 

Third: Ubuntu and it's official distributions, all have fairly wide compatibility for sound cards, touch pads, sound cards, NIC cards, and the like. Even video drivers come standard. The Default for GeForce cards is the X.Org X Server - Nouveau generic display driver.

 Fourth: If you select Lubuntu(which is the fastest, and least demanding) be aware that you'll need to manually start the Network Manager App. This can be done during the install by going to Run in the equivalent of the start menu and type "nm-applet" with out the quotation marks. To have it start on start up you go into Default applications for LXSession under Preferences in the "Start Menu." Go to the Autostart tab type nm-applet in the text box next the +Add button then click the +add button.   Hope that all helps.

---

### Post by mastablasta on 2014-09-23
what grahics card do you have inside?

how much RAM?

drivers in Linux are part of kernel (core) of the OS. some proprietary/closed source drivers might need to be installed later on (typically Wi-Fi, GPU chip drivers, touchpad occasionally). it is best to have a wired internet connection available during install.

you can try the OS before installing. on boot select try it. it will load the OS into ram. all changes made are lost on reboot (except if you write something to local hard disk). you can see hwo well it works and if it needs a any additional drivers.

note that Ubuntu needs GPU that offers good 3D hardware acceleration. otherwise it will be very slow. several ways around this but easiest is to try a lighter desktop such as those found in lighter version of Ubuntu - Xubuntu, Lubuntu...

---

### Post by kira-yamato-2008 on 2014-09-23
> **mastablasta said:**
> what grahics card do you have inside?

how much RAM?

drivers in Linux are part of kernel (core) of the OS. some proprietary/closed source drivers might need to be installed later on (typically Wi-Fi, GPU chip drivers, touchpad occasionally). it is best to have a wired internet connection available during install.

you can try the OS before installing. on boot select try it. it will load the OS into ram. all changes made are lost on reboot (except if you write something to local hard disk). you can see hwo well it works and if it needs a any additional drivers.

note that Ubuntu needs GPU that offers good 3D hardware acceleration. otherwise it will be very slow. several ways around this but easiest is to try a lighter desktop such as those found in lighter version of Ubuntu - Xubuntu, Lubuntu...

You're correct on that, also with GeForce GPUs especially the 8000 series, the Unity Desktop Environment will cause screen flicker. Also the Nvidia Binary drivers cause lock ups on all Linux Systems with the lower level 8000 series GPUs. So there's not real fix for it.

---

### Post by Mike_Walsh on 2014-09-23
The other two are right about the Nvidia drivers; it's another example of Dell's use of unorthodox hardware!

I have an even older Inspiron than yours; an 1100, from 2002. The Intel graphics chipset is an absolute nightmare to work with, so you're not alone in this respect.

You probably WOULD be better with either Xubuntu, or Lubuntu. They're a lot lighter in their hardware-specific requirements, and as mastablasta says, they don't need 3D acceleration; an important point with older systems.

Regards,

Mike.

---

### Post by mörgæs on 2014-09-23
> **kira-yamato-2008 said:**
> Fourth: If you select Lubuntu(which is the fastest, and least demanding) be aware that you'll need to manually start the Network Manager App. This can be done during the install by going to Run in the equivalent of the start menu and type "nm-applet" with out the quotation marks. To have it start on start up you go into Default applications for LXSession under Preferences in the "Start Menu." Go to the Autostart tab type nm-applet in the text box next the +Add button then click the +add button.   Hope that all helps.

No, this is fixed in Lubuntu 14.04.1. Anyway, a good general rule is to install using wired internet access and apply all updates before focusing on the wirefree.

---

### Post by kira-yamato-2008 on 2014-09-23
> **mörgæs said:**
> No, this is fixed in Lubuntu 14.04.1. Anyway, a good general rule is to install using wired internet access and apply all updates before focusing on the wirefree.

Oh they did fix it already? That's great! Thanks for correcting me, now I know, so when I decide to reinstall Lubuntu I don't have to worry about it. Thank you!

> **Mike_Walsh said:**
> The other two are right about the Nvidia drivers; it's another example of Dell's use of unorthodox hardware!

It's not a Dell specific problem actually. I have an HP with a GeForce 8200M G and I have the problem. People with Toshiba, Lenovo, and other computers that sport a GeForce 8000 series Mobile GPU seem to have the issue, and it reports across all Linux distros. Nobody, not even Nvidia seems to know what the underlying issue is.

---

### Post by fleawhale on 2014-09-25
Have installed Lubuntu and it's working like a dream compared to Windows Vista.
Wired internet access during setup was definitely a good idea to get the Broadcom B43 wireless driver...
Thanks to all for your advice!

---

### Post by kira-yamato-2008 on 2014-09-25
Well since your question is answered please mark this thread as solved. You can do that by editing your first/original post in this thread, and selecting the drop box listed under "Prefix:" and selecting [SOLVED] in the drop down list.

---

