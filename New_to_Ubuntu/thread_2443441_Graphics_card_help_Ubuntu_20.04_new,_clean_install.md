---
title: "Graphics card help Ubuntu 20.04 new, clean install"
date: 2020-05-15
forum: New to Ubuntu
---

### Post by Joe_Martin on 2020-05-15
I just installed 20.04 mate and my graphics card did not install automagically on an ubuntu install for the first time. Little lost. Details are below on my hardware.


Can someone assist with the driver I need to install? Thanks.


@ubuntumate:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Stoney [Radeon R2/R3/R4/R5 Graphics] (rev eb)

---

### Post by fhesseti on 2020-05-15
What happens when you open the driver manager?

---

### Post by Joe_Martin on 2020-05-15
It is not recognized (unfortunately).  That's the first thing I tried.

---

### Post by CelticWarrior on 2020-05-15
AMD and Intel drivers are open-source and installed automatically. No user action required.

---

### Post by Joe_Martin on 2020-05-15
I can't run marco's compositor and as a result, no accelerated graphics.  There is no driver to allow me to run compositor?

---

### Post by CelticWarrior on 2020-05-15
What is the problem exactly?

---

### Post by Joe_Martin on 2020-05-15
Yes, ubuntu mate 20.04 clean install.  Sorry, I thought I mentioned that in 1st post....

---

### Post by Joe_Martin on 2020-05-15
I have installed ubuntu on this Dell before and video card always installed automatically, until this clean install of ubuntu mate 20.04.  Had to start in safe graphics mode and manually changed marco to No Compositing due to accelerated graphics not being installed during initial install.

---

### Post by CelticWarrior on 2020-05-15
Safe graphics overrides graphics drivers so no hardware acceleration is an expected consequence. The question is what made you do that... What problem were you having?

---

### Post by Joe_Martin on 2020-05-15
After initial install, total video graphic tearing.  Welcome screen was broken up and spreading all over monitor. Not readable.  So, I restarted post install in safe graphics mode, turned off composting so it would be usable.

---

