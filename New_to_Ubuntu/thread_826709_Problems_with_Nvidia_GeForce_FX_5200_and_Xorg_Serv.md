---
title: "Problems with Nvidia GeForce FX 5200 and Xorg Server"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by gcg on 2008-06-12
I upgrade to Ubuntu 8.04 just a week ago, ever since i've been trying to install the drivers from nVidia (NVIDIA-Linux-x86-171.06.01-pkg1.run (Latest actual Driver))and configure my xorg.conf (/etc/X11/xorg.conf)so i can get my effects and d'like.  So far try sudo gedit /etc/X11/xorg.conf , sudo dpkg-reconfigure -phigh xserver-xorg and so on...  Nothing yet, all i get is resolutions with no way to low down (320x..) or a bunch of lines that makes it impossible to see the desktop.  So far i haven't have the problems the others had, like black screen etc etc etc.  But the problem of not been able to activate the "EFFECTS", not been able to obtain the resolution 1280x800 or 1029x768, and the Xserver, glx (even thought is mark Load "glx", this have be come agravated.  I din't had this problems on Ubuntu 7.10.

Can anybody please help me on this.  Followed is the description of my BOX:
1) Soyo Dragon Platinum Edt
2) 1 GB of RAm DDR 333
3) Lynksys NIC Card
4) 3000 AMD CPU
5) nVidia GeForce FX 5200 128MB DDR AGP (Connection)

Thanks for helping in advanced.  NOTE: Please provide with step by step since i'am a totall newb on Open Source Distro.  I have Open Suse 10.3 on my Laptop Toshiba with no problem at all's.

---

### Post by Joeb454 on 2008-06-12
I don't think the *latest* drivers support that card as it's pretty old (I have on in another desktop of mine).

Do the drivers from synaptic not work? And is there nothing in System &#8594; Administration &#8594; Hardware Drivers?

---

### Post by alienexplorers on 2008-06-12
Use Envy and delete your current driver.  Install in manual mode the 96.xx.xx drivers.  This driver works perfectly on my fx5200.  Gives full use of compiz and all other graphic effects such as screen savers.

---

### Post by argail1980 on 2008-06-12
I have the same card and the effects do work. maybe you have the wrong driver version installed..

can you somehow uninstall them? then you can simply do a 

```
apt-get install nvidia-glx
```

There are two more packages. nvidia-glx-new and -legacy. maybe you card just "changed packages", so that it's now supported by the lecacy drivers.

post your xorg.conf, maybe there's an error here

---

### Post by tenmoi on 2008-06-12
don't know how you installed the driver first time. But this is the way I always do it.

This is the newest 32 bit driver for your chipset: [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/NVIDIA-Linux-x86-173.14.05-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/NVIDIA-Linux-x86-173.14.05-pkg1.run)

remove all traces of Linux-restricted-modules*
sudo apt-get install build-essential libxft-dev.
Alt + Ctrl + F1
sudo /etc/init.d/gdm stop
sudo sh path to your driver.run --uninstall # skip this step if you did not install it.
sudo sh /path to your driver.run 
hit accept/yes all the way.
sudo /etc/init.d/gdm restart.

post back here your result.

bie.

---

### Post by alienexplorers on 2008-06-12
Just use ENVY and save yourself a lot of problems.

---

### Post by gcg on 2008-06-12
Envy Is Not Working For Me, I Try Envyng Wich Is For Ubuntu 8.04, And Still...  Plus In Synaptic U Have 2 Envy's Ng, Wich One Should I Used?

---

### Post by gcg on 2008-06-12
I Tried That Too, And It Din't Work..  Plus Ubuntu 8.04 Do Not Used Xfree, It Used Xorg.conf

---

### Post by alienexplorers on 2008-06-12
You neeed to load both ENVY files (envy-ng & I believe envy-gtk)

---

### Post by gcg on 2008-06-12
I Have In Synaptic 4 Nvidia-glx-new, Wich One Should I Pick?

---

### Post by gcg on 2008-06-12
The Driver 96... It Crash While Installing.

---

### Post by alienexplorers on 2008-06-12
Just rerun it.

---

### Post by alienexplorers on 2008-06-12
Have you gotten the driver to load?  If so, is it working OK?  If not you could posssible load the driver by doing:
> sudo aptitude install nvidia-glx

---

### Post by bijeeshvs on 2008-06-12
you should try nvidia-glx insted of nvidia-glx-new
may be thats ur problem

---

### Post by gcg on 2008-06-12
> **alienexplorers said:**
> have You Gotten The Driver To Load?  If So, Is It Working Ok?  If Not You Could Posssible Load The Driver By Doing:

Men Somethiing Is Really Wrong Here, Look I'm Gonna Send U My Xorg.conf File, Can I!?

---

### Post by bijeeshvs on 2008-06-12
dont worry
in command mode type

sudo apt-get install envyng-gtk
 then start it with command
envyng -t
uninstall the driver from the menu
and install driver in automatic mode  

not on a linux machine right now......................

---

### Post by bijeeshvs on 2008-06-12
find envy here

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

i think its the best way to solve your problem..............

---

### Post by argail1980 on 2008-06-12
yeah, please post the xorg.conf

and I also think it is the nvidia-glx package, not the "new" one

@alienexplorers: will envy remove a manually installed driver?

---

