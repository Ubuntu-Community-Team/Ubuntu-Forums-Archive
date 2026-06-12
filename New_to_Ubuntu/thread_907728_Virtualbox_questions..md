---
title: "Virtualbox questions."
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-09-01
So i wanted to get virtual box to run all of my games(I tried Wine but just had to many problems). I had a few questions though. When you dedicate RAM and video memory to your virtual system, after the system is turned off, the memory will go back to the host(ubuntu) system right? I am almost sure it will, but would like to make sure. Also, under settings, the most video memory that can be allocated is 128MB, i have a 512MB card, so i can easily, and would like to put much more then this into the virtual machine because i will be using it only for gaming. In the user manual it says

"Better video support While the virtual graphics card which VirtualBox emulates for
     any guest operating system provides all the basic features, the custom video
     drivers that are installed with the Guest Additions provide you with extra high
     and non-standard video modes as well as accelerated video performance. In
     addition, with Windows and recent Linux, Solaris and OpenSolaris guests, when
     the Guest Additions are installed, you can resize the virtual machine&#8217;s window,
     and the video resolution in the guest will be automatically adjusted (as if you
     had manually entered an arbitrary resolution in the guest&#8217;s display settings).
"

Has anyone gone through and made a "guest addition"? Is this easy to do? I am fairly new to Ubuntu, but know my way around, but this is my first experience with VirtualBox. 

The main thing i am trying to get at is making sure my games will run smoothly, and have plenty of video memory for nice graphics.

Any help on this would be awesome.

---

### Post by django0909 on 2008-09-01
I don't know a thing about Virtual Box. However, the Wine AppDB, [http://appdb.winehq.org/](http://appdb.winehq.org/), has fairly up to date info on what Wine will and won't run, and how to iron out problems.

Perhaps that will help?

--django

---

### Post by swoll1980 on 2008-09-01
Vbox emulates a 4mb graphics card so your chances of getting a game post 1998 to work on it are not that great

---

### Post by Codemastadink on 2008-09-01
> **django0909 said:**
> I don't know a thing about Virtual Box. However, the Wine AppDB, [http://appdb.winehq.org/](http://appdb.winehq.org/), has fairly up to date info on what Wine will and won't run, and how to iron out problems.

Perhaps that will help?

--django

Ive looked into this, and tried many tires to work out problems, but for some reason wine will just not work for some of my major games. Its very frustrating because i want to be able to use wine instead of VirtualBox, but i have just had a lot of problems with it.

---

### Post by django0909 on 2008-09-01
I've resigned myself to the fact that Wine just doesn't like some stuff...

---

### Post by tuxxy on 2008-09-01
I dont think  you will be able to any run high end games in a virtual environment.

---

### Post by niccholaspage on 2008-09-01
Virtualbox Doesn't have 3D Hardware Acceleration.Even if you install guest additions you will not be able to use all if your video memory.

---

### Post by knattlhuber on 2008-09-01
> **Codemastadink said:**
> Has anyone gone through and made a "guest addition"? Is this easy to do? I am fairly new to Ubuntu, but know my way around, but this is my first experience with VirtualBox.

Installing the guest additions isn't too difficult. You downloaded the 'guest addition' image and mount it through
Devices > Mount CD/DVD-ROM > CD/DVD-ROM image

Once mounted you run either the Linux script (for Linux additions) or the .exe file (for Windows additions) inside your virtual machine.

---

