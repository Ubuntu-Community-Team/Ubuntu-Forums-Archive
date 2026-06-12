---
title: "installing video drivers in ubuntu"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by yasirmahmood on 2011-12-07
hey i have internal card on my motherboard my motherboard is dg41 how can i install video drivers on ubuntu 11.10 please help me out and do tell me that is there something like taskmanager in ubuntu to check whether all of my drivers have been detected or not please do reply thanks in advance

---

### Post by wolfen69 on 2011-12-07
If you go to *Additional Drivers*, it will let you know if there are any drivers available.

---

### Post by josephmills on 2011-12-07
There are a bunch of ways of doing this but could you please open up your terminal and enter 
```
lspci -nn | grep VGA 
``` and paste here so we can see if there is maybe a hybrid or some sort of mod/driver 
thanks 
Joseph

---

### Post by Mark Phelps on 2011-12-08
According to Google, your motherboard is using an onboard Intel GMA4500 graphics chip -- for which the drivers have ALREADY been installed in your PC.  You do not need to install video drivers -- this is Linux, not Windows.

---

### Post by yasirmahmood on 2012-10-30
> **josephmills said:**
> There are a bunch of ways of doing this but could you please open up your terminal and enter 
```
lspci -nn | grep VGA 
``` and paste here so we can see if there is maybe a hybrid or some sort of mod/driver 
thanks 
Joseph

yeah dear it says 
"     0:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
"

---

### Post by NikTh on 2012-10-30
> **yasirmahmood said:**
> yeah dear it says 
"     0:02.0 VGA compatible controller [0300]: **Intel Corporation 4 Series** Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
"
Hi ,
is what Mark Phelps said
> **Mark Phelps said:**
> According to Google, your motherboard is using an onboard Intel GMA4500 graphics chip -- **for which the drivers have ALREADY been installed in your PC.  You do not need to install video drivers** -- this is Linux, not Windows.
:)

Thanks

---

### Post by yasirmahmood on 2012-10-30
> **NikTh said:**
> Hi ,
is what Mark Phelps said

:)

Thanks


ya dear i know its linux but its not recognizing my monitor and shows only two desktop resolution  change options, just 1024 * 768 and 800 * 600
moreover thats the reason if i try to turn on desktop 3d effects they dont work i remember when i installed mandriva linux it installed my drivers and 3d effects worked just fine

---

### Post by Impavidus on 2012-10-30
When I bought a new laptop a year ago and installed 10.04LTS I also had issues with my graphics, including not being able to switch to the correct display resolution and very slow (not hardware accelerated) 3D graphics. No extra drivers were available. Most of the issues were solved by upgrading to the latest ubuntu version, the few remaining problems disappeared after a few normal updates.

---

### Post by Mark Phelps on 2012-10-30
> **yasirmahmood said:**
> ya dear i know its linux but its not recognizing my monitor and shows only two desktop resolution  change options, just 1024 * 768 and 800 * 600
moreover thats the reason if i try to turn on desktop 3d effects they dont work i remember when i installed mandriva linux it installed my drivers and 3d effects worked just fine

OK, then read the link below about Mandriva:

[http://communities.intel.com/thread/18929]("http://communities.intel.com/thread/18929")

That shows the Intel video driver: xserver-xorg-video-intel

To see if that is the case, open a terminal and enter "sudo apt-cache search xserver-xorg-video-intel"

If it's not installed, you can install it by entering that package name in the Software Center.

There is no other drive you can use.

---

### Post by yasirmahmood on 2012-10-31
> **Mark Phelps said:**
> OK, then read the link below about Mandriva:

[http://communities.intel.com/thread/18929](http://communities.intel.com/thread/18929)

That shows the Intel video driver: xserver-xorg-video-intel

To see if that is the case, open a terminal and enter "sudo apt-cache search xserver-xorg-video-intel"

If it's not installed, you can install it by entering that package name in the Software Center.

There is no other drive you can use.

hey thanks for ur reply well it was installed but debug file was not install so i install it too any way if its installed then why its not recongnizing my monitor ??

---

### Post by Mark Phelps on 2012-10-31
> **yasirmahmood said:**
> hey thanks for ur reply well it was installed but debug file was not install so i install it too any way if its installed then why its not recongnizing my monitor ??

If you mean that in the Display app, your monitor shows up as something like "generic xxx"; sorry, mine does the same thing.  

In my case, I can get display resolution up to the max the monitor supports -- 1280x.

Monitors don't actually use drivers, so I don't know how to force yours to be recognized properly.

---

