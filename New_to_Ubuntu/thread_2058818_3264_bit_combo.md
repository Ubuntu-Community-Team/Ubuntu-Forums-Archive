---
title: "32/64 bit combo"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by MasterJimmy on 2012-09-16
im running a 64 bit rig but am having weird issues with my 64 bit 12.04 install. im considering dropping back to a 32 bit install. if i do so will it work? and as i have a 64 bit proc will i get better performance out of it?

---

### Post by mcduck on 2012-09-16
Yes, you can run a 32-bit operating system on a 64-bit processor, but you will of course loose the performance improvements, ability to use more than 4GB RAM (without PAE kernel) and any other benefits you get from a 64-bit system.

If it makes a difference or not of course depends on what you use your computer for, but I'd recommend trying to sort out the problems with your 64-bit system instead (especially since the problems might not even be related to the 64-bit version, hard to say without knowing what exact kinds of problems you are having with the system...)

---

### Post by MasterJimmy on 2012-09-16
> **mcduck said:**
> Yes, you can run a 32-bit operating system on a 64-bit processor, but you will of course loose the performance improvements, ability to use more than 4GB RAM (without PAE kernel) and any other benefits you get from a 64-bit system.

If it makes a difference or not of course depends on what you use your computer for, but I'd recommend trying to sort out the problems with your 64-bit system instead (especially since the problems might not even be related to the 64-bit version, hard to say without knowing what exact kinds of problems you are having with the system...)

all i have is 4 gb ram so the limit isnt an issue. the issues i have is a whole bunch of display issues like stuff staying on the screen like the labels for the launchbar apps and the like.

---

### Post by MasterJimmy on 2012-09-16
> **MasterJimmy said:**
> all i have is 4 gb ram so the limit isnt an issue. the issues i have is a whole bunch of display issues like stuff staying on the screen like the labels for the launchbar apps and the like.


basicall i just use it for watcing videos and some flash gaming mostly. some word processing and music. and i do play a bunch of games i get from the software center. what benefits does 64 have over 32? my main question is if what i do will go faster since the proc will be running a 32 bit system?

---

### Post by oldos2er on 2012-09-16
Sounds like a graphics issue rather than bitness. What video card do you have?

---

### Post by MasterJimmy on 2012-09-16
> **oldos2er said:**
> Sounds like a graphics issue rather than bitness. What video card do you have?
whatever came in the laptop. a Gateway NV53A52u. i tried to enable the restricted drivers but all that did was screw up the screen alignment and the only way i could fix it was to completely reinstall the system

---

### Post by mcduck on 2012-09-16
> **MasterJimmy said:**
> basicall i just use it for watcing videos and some flash gaming mostly. some word processing and music. and i do play a bunch of games i get from the software center. what benefits does 64 have over 32? my main question is if what i do will go faster since the proc will be running a 32 bit system?

Things will run slower, or at same speed, than they do with a 64-bit system (depending on if the programs you are using are made in a way that allows them to benefit from 64-bit processing).

Anyway, I agree with oldos2er, that sounds like the issues are more related to your graphics card and/or it's drivers, in which case switching to 32-bit version wouldn't help.

---

### Post by oldos2er on 2012-09-16
> **MasterJimmy said:**
> whatever came in the laptop.

Can you run ```
lspci | grep VGA
``` in a terminal, and post the output? It'll tell us exactly what we're dealing with.

---

### Post by MasterJimmy on 2012-09-16
> **oldos2er said:**
> Can you run ```
lspci | grep VGA
``` in a terminal, and post the output? It'll tell us exactly what we're dealing with.


james@AndriodLT:~$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
james@AndriodLT:~$

---

### Post by oldos2er on 2012-09-17
There are some suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=1857911](http://ubuntuforums.org/showthread.php?t=1857911)

---

