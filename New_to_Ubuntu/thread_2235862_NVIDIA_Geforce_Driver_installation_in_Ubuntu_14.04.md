---
title: "NVIDIA Geforce Driver installation in Ubuntu 14.04"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by mithun6 on 2014-07-23
Hi, i have got a i3 processor with 4 gb ram and 2 gb NVIDIA GEFORCE video card, will i be able to install the drivers of my graphic card for ubuntu 14.04, please help

---

### Post by kc1di on 2014-07-23
I'm running Nvidia here with no problems,  you can use the additional drivers tool to install the nvidia driver you need after you install ubuntu.

it's found by going to software center >edit>software sources>additional drivers -- it takes a minute or two analyse your card and presents you with choices that should work with your card.  Good Luck ;)

---

### Post by buzzingrobot on 2014-07-23
There's more involved with installing an Nvidia driver than just dropping a file in a directory, so the process in Additional Drivers can take several minutes. Sometimes people think it times out and so they quit the program, which usually leaves things in a broken mess.

---

### Post by RedRat on 2014-07-23
I have a question here. I have an Nvidia GeForce card and I am running the driver that is non-proprietary that loaded when I installed 14.04. The computer runs fine and the graphics are very good. What do I really gain in running the proprietary Nvidia Driver? I kind of come from the school that if it ain't broke, don't fix it!

---

### Post by webercs1 on 2014-07-23
RedRat, I would aggree with your assesment about ain't-broke.  

If the install is working for you, then don't monkey with it unless you are ok with possibly going down an advanced route to fix it, should it get hosed.

---

### Post by RedRat on 2014-07-23
> **webercs1 said:**
> RedRat, I would aggree with your assesment about ain't-broke.  

If the install is working for you, then don't monkey with it unless you are ok with possibly going down an advanced route to fix it, should it get hosed.

Thanks. Over the years that is something I have learned the hard way:p


I really did wonder what the proprietary drivers offered over the ones that came with the install. I do remember, ever since my 7.04 days way back when, that installing video drivers seem to lead to more problems, and then comes the fixing. My advice to those who have installed 14.04 and are satisfied with their screens, just keep it going. I have a 27" Samsung monitor and the non-proprietary drivers give me a 1920x1200 resolution, that is the native resolution of the monitor. Until I get information otherwise, I will live with what I have.

---

### Post by kc1di on 2014-07-24
RedRat - It my policy also. But for many the open source driver does not work with their card,  That's the case on this machine. Your fortunate to have a nvidia card that seems to work well with it. 

Have fun :)

---

### Post by oldrocker99 on 2014-07-24
I have discovered that (as usual with these things) games run best with the newest nVidia driver (3.40.25). To install it:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install dkms nvidia-graphics-drivers-340
``` 

dkms, BTW, is the program that will link the nVidia (and any other proprietary drivers) to any new kernel installed in an upgrade, so you don't have to reinstall the video driver.

Good luck!

---

### Post by sp40140 on 2014-07-24
@oldrocker.. this dkms thingy.. does it work with Radeon drivers as well or is it specific to Nvidia only?

---

### Post by RedRat on 2014-07-24
> **kc1di said:**
> RedRat - It my policy also. But for many the open source driver does not work with their card,  That's the case on this machine. Your fortunate to have a nvidia card that seems to work well with it. 

Have fun :)

Good point. My NVidia card came with my rather older (5-6 yr old HP Pavilion computer, a Geforce 9800) so that may well be the reason the non-proprietary driver works with it, they have had more time to tweak the driver. I imagine that brand new cards in the series may be more difficult to get all the bugs out. My graphics card has been bouncing around for quite some time.

---

### Post by mithun6 on 2014-07-27
Thank you for the quick responses guys, i will try and install the drivers, still i have a doubt that i wont able to play games as in windows right?
and can you tell me please how OS zorin can help you with gaming?
Thank you

---

### Post by yancek on 2014-07-27
A lot of games are written and designed to be run on windows.  You may be able to get many or at least some to work using the wine application or playonlinux.  Wine has its own website with a listing of games which play well, ok, not well.

 [http://winehq.org](http://winehq.org)

---

### Post by buzzingrobot on 2014-07-27
It's unlikely the running Windows games on Linux via Wine or PlayOnLinux will give you an experience preferable to running them on Windows.  Whether it is good enough for you depends. 

An increasing number of games are becoming available as native Linux apps, particularly using Steam.

---

### Post by kira-yamato-2008 on 2014-07-27
My issue is that running a proprietary driver or the open source version there causes my machine to hard lock when accessing the video card for videos, 3D rendering in OpenGL, or anything that makes any demand of the video card. Not including gaming the open source Nouveau driver does everything else I want it to.

---

