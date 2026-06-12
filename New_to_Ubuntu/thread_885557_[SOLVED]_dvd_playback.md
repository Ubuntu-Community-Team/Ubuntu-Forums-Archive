---
title: "[SOLVED] dvd playback"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by DarinB on 2008-08-10
i am about to install hardy 64 on a friends core 2 duo
do i need libdvdcss to playback store bought dvd's?????
Do i need to use hardy 64 at all on a core2 duo what is the benefit over Hardy i386???

---

### Post by SunnyRabbiera on 2008-08-10
> **DarinB said:**
> i am about to install hardy 64 on a friends core 2 duo
do i need libdvdcss to playback store bought dvd's?????
Do i need to use hardy 64 at all on a core2 duo what is the benefit over Hardy i386???

Basically yes libdvdcss is needed to play most commercial DVD's.
But as for the choice of 64 vs 32 bit version of hardy I would go 32, things still need to be done in the 64 bit version to make things work they way the should without tweaking... like a miracle.

---

### Post by pparks1 on 2008-08-10
Yes, you will need to install libdvdcss to play any commercially purchased DVD.   CSS is Content Scrambling System that DVD's use to protect the content.  libdvdcss is the decrypting portion that allows your player to see the actual content.

You do NOT need a 64 bit operating system on a core2duo.  That processor will run both 32 and 64 bit operating systems.   Advantages of 64-bit include more speed (depending upon function) and ability to address 4GB of RAM or more.   The downside is driver support, the code takes about 2x as much RAM so you actually should run with more, and some apps have to run in a compatibility mode which doesn't always lead to the best experience.

My suggestion:  Stick with 32-bit for awhile longer yet.

---

### Post by DarinB on 2008-08-10
will she get the same performance???
all she really dose is browse the web play videos and write emails
an occasional document????
she was on gutsy but i tried to upgrade her but it failed now a have to do a clean install of hardy i burned a 8.04.1 of both amd64 and i386...

---

### Post by SunnyRabbiera on 2008-08-10
> **DarinB said:**
> will she get the same performance???
all she really dose is browse the web play videos and write emails
an occasional document????
she was on gutsy but i tried to upgrade her but it failed now a have to do a clean install of hardy i burned a 8.04.1 of both amd64 and i386...

Yeh performance wont be an issue no matter what you do, though the 32 bit kernel does have its limitations such as going over 4 GB of memory but hopefully in the near future a 64bit system will be a viable option as soon as certain companies get their acts straight *cough*adobe*hack* *cough*microsoft*hack*

---

### Post by DarinB on 2008-08-10
thanks that clears it up for me.
she only has 2Gb of ram and will never add more, so for her needs 32bit system will save me a lot of headaches and phone calls.
thanks again.

---

