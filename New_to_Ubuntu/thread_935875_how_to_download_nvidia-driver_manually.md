---
title: "how to download nvidia-driver manually???"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by vikas.368 on 2008-10-02
presently I am using ubuntu 8.04..
my graphic card is NVIDIA(R) GeForce(R) 8600M GT


initially i installed nv-driver using package manager..but after installing that it prompted "system restart requiered"...then i i restarted my laptop.

but after restarting my entire ubuntu os crashed.i got a white blank page instead of login page.
then i stalled ubuntu again.
now i want to install nv-driver manually.
p[lease give a solutin

---

### Post by Archmage on 2008-10-02
Do you want to use Envy?

---

### Post by mike1234 on 2008-10-02
> **vikas.368 said:**
> presently I am using ubuntu 8.04..
my graphic card is NVIDIA(R) GeForce(R) 8600M GT


initially i installed nv-driver using package manager..but after installing that it prompted "system restart requiered"...then i i restarted my laptop.

but after restarting my entire ubuntu os crashed.i got a white blank page instead of login page.
then i stalled ubuntu again.
now i want to install nv-driver manually.
p[lease give a solutin


 Download nvidia driver from their website and execute following commands:

Logout > Ctrl-Alt-F1 and switch to a tty and login

sudo /etc/init.d/gdm stop

sudo sh NVIDIA-Linux-x86-171.06-pkg1.run

Ctrl-Alt-Del for PC restart 			 		

M.

---

### Post by vikas.368 on 2008-10-02
> **Archmage said:**
> Do you want to use Envy?
what is this envy??

---

### Post by vikas.368 on 2008-10-02
> **Archmage said:**
> Do you want to use Envy?
i want to enable extra desttop effects.
i installed compiz but , i am not getting any effects of cube or anything.
nothing is woking.

---

### Post by Sef on 2008-10-02
1) Moved to absolute beginners.   

2) What does System > Administration > Hardware Drivers say about the drivers?  8600 almost always do just fine.

---

### Post by oldos2er on 2008-10-02
> **vikas.368 said:**
> what is this envy??

 [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by bumanie on 2008-10-02
The nvidia 8600 should work fine with ubuntu via the hardware divers download. System --> Administration --> Hardware drivers and click the box to enable the card. A driver will then download. I have a 8600GT and it works fine with the hardware driver. Manually installing gpu drivers means that any time there is a kernel upgrade, you will have to manually reinstall the driver each time. IMO, this method should only be used as a last resort - but in your case, the 8600GT should work OK.

---

