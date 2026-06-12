---
title: "What is better supported Nvidia or AMD now"
date: 2011-08-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ToxicBurn on 2011-08-09
linux is a hobby OS for me and after some really bad times with linux the past year with the guys who keep breaking 3d support each and every release i am not sure i should even ask but as of today who is better supported now 

AMD or Nvidia ?

I have a AMD HD 6850 
and a Nvidia GTX 560 

if i was to play with linux again what would be my best choice for driver support ?

thanks for the input

---

### Post by cbowman57 on 2011-08-09
Nvidia for sure.

AMD/ATI cards have been having problems.

---

### Post by t1497f35 on 2011-08-09
Accelerated video in Flash is available only through VDPAU which so far is only supported by Nvidia's binary driver - this driver has also the best OpenGL support, so for a typical desktop user "Nvidia + their proprietary driver" is the best choice.

If you want to use open source drivers - then Intel and ATI are better.

---

### Post by ToxicBurn on 2011-08-09
thank you guys

---

### Post by kaldor on 2011-08-09
AMD works fine these days.

---

### Post by Redblade20XX on 2011-08-09
Testing 11.10 got my new laptop running perfectly with the open source ATI drivers.

-Red

---

### Post by ELD on 2011-08-10
I find AMD cards much nicer to use even if flash isn't accelerated it still works perfectly fine.
 
AMD drivers seem to be easier to install and configure too.
 
AMD also has the best open source support...

---

### Post by rapiertg on 2011-08-10
Long time i haven't use nvidia on Linux, but i can say a bit of AMD cards, as i have two of them. HD 38xx and HD 4650.

 If you want to play some modern games than you should forget about open source ones, as most of them just don't work ( trine, aquaria, braid, heroes of newerth, and lot more) becouse of lack of features. Its performance is also not that good yet.

fglrx is good , but nothing more than good. It still have annoying bugs. Gnome-shell bug makes new Gnome environment almost unusable. There is also a bug with lwjgl engine on 32bits systems that crashes java games (minecraft, spiral knights etc.)

If it was me to choose i would take nvidia card, because i had a lot less probs with them. But as i said i haven't tested it for some time...

PS. If you are completely not interested in games i don't see any differences between these two vendors.

---

### Post by kaldor on 2011-08-10
> **ELD said:**
> I find AMD cards much nicer to use even if flash isn't accelerated it still works perfectly fine.
 
AMD drivers seem to be easier to install and configure too.
 
AMD also has the best open source support...

This. It works fine for most people.

If you aren't on a laptop and don't play 3d games, AMD is the perfect choice. That said, the default open source drivers work pretty nicely in a lot of games.

---

### Post by jerrylamos on 2011-08-10
> **cbowman57 said:**
> Nvidia for sure.

AMD/ATI cards have been having problems.

As a computer engineer, the other way around.  AMD/ATI were running when someone made some code changes.  It's the "new code changes" that are broken.

Jerry

---

### Post by ratcheer on 2011-08-10
My ATI card is fine with Natty. However, I cannot run Unity (3D) in Oneiric.

Tim

---

### Post by sgage on 2011-08-10
My NVIDIA GeForce 8500 GT card works beautifully with the nvidia-current drivers. Does everything it is rated to do. 

The astronomy program Stellarium is a nice test - fairly demanding. With the nouveau open-source drivers with "experimental 3D" abilities installed, it works in a flickery, stuttering way. With the proprietary drivers, it's as smooth as silk.

Also, the nouveau drivers run a solid 12+ degrees C hotter than nvidia-current. Not so good.

---

### Post by jerrylamos on 2011-08-10
> **cbowman57 said:**
> Nvidia for sure.

AMD/ATI cards have been having problems.

As a computer engineer, the other way around.  AMD/ATI were running when someone made some code changes.  It's the "new code changes" that are broken.

Jerry

---

### Post by cariboo on 2011-08-11
> **jerrylamos said:**
> As a computer engineer, the other way around.  AMD/ATI were running when someone made some code changes.  It's the "new code changes" that are broken.

Jerry

The ATI/AMD devs haven't released a working driver until the last few weeks of the development cycle, for the last 3-4 releases. Ubuntu usually gets a new ATI/AMD driver before its officially released, to give Alberto time to package it, if anything place the blame on the developers, nVidiia seems to be able to release working drivers despite the changes being made in each release.

---

### Post by Harry33 on 2011-08-11
I have these two 64-bit setups:
- Nvidia with proprietary drivers
- ATI with open source drivers
Both setups run with gnome-shell (unity purged)

I have experienced less troubles with ATI open source drivers than with Nvidia.
Latest was the issue with gl enabled cairo (nvidia proprieatary drivers).
However Nvidia is superb regarding speed, smooth operation and rendering.

---

### Post by kayosiii on 2011-08-11
> **jerrylamos said:**
> As a computer engineer, the other way around.  AMD/ATI were running when someone made some code changes.  It's the "new code changes" that are broken.

Jerry

It depends on exactly what broke and why. The new code may have done something wrong or it may have triggered a bug in the drivers. If the later is the case then It is much better to fix the drivers than to hack around the problem in Gnome since a fix in the drivers makes everybody elses life easier too.

---

### Post by 3vi1 on 2011-08-11
I'll throw in my two cents and say the nVidia drivers are better supported.  When the XOrg ABI has been revved in the past, it has seemed like it takes forever to get the AMD/ATI drivers updated.

If you've ever tried to completely uninstall the AMD/ATI drivers and install another type of card, you know what a nightmare that can be.  I've had to go in and manually delete broken files/symlinks after removing the AMD drivers on the couple of occasions I was testing a system with both types of cards

In there defense, it's been nearly a year since I last subjected myself to the ATI/AMD pain.  It's too bad the situation is as it is, as the ATI stuff is more friendly to open-source - but you don't want the open drivers if you plan to game with Wine (or even with some native apps.

---

### Post by jwbrase on 2011-08-11
From my experience, ATI isn't bad at all with Direct3D on Windows, but is subpar for OpenGL under both Windows and Linux. Since native Linux software doesn't use Direct3D, an NVidia card is preferable.

---

