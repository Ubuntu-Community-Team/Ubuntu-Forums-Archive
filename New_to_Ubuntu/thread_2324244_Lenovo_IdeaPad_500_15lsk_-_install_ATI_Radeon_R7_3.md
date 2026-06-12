---
title: "Lenovo IdeaPad 500 15lsk - install ATI Radeon R7 360"
date: 2016-05-12
forum: New to Ubuntu
---

### Post by Jan_Corba on 2016-05-12
Hi guys,
first of all- I am new in Linux. I needed OS for work with videos and photos, so I choosed Ubuntu Studio. I was trying Windows 8.1, but it is so slow in converting videos (I thing that hardware is good enought), that I would like to try Linux.
Installing was easy, but setting things in this OS is pretty hard form me.
First of all, I want to install driver for ATI Radeon R7 360, cause I will need to use these card for better performance.
I tryed install ATI_crimsom_installator_driver-15.302. I generaded driver package, install it and reboot. But system don`t boot any more.
Just black screen shows and writes- /dev/sda2: clean, 325936/60506112 files, 6316981/241998336 blocks.
What I did wrong? Should I use other way to install drivers?
Another question is- laptop has 2 graphic cards- Intel HD graphics 520 and ATI radeon R7 360. Do you thing, that Linux will able to switch between this 2 cards?
Or, how I can switch it manualy, to use ATI?
Thank you for answer.

---

### Post by QIII on 2016-05-12
Hello!

The first thing we'll need to know is what release of Ubuntu you are using.

---

### Post by Jan_Corba on 2016-05-12
I am using last release ubuntustudio-16.04-dvd-amd64.

---

### Post by grahammechanical on 2016-05-12
You should install Ubuntu 14.04.4. The reason? AMD are not providing proprietary video drivers for 16.04. And this is because Ubuntu 16.04 has upgraded the X server to 1.18 and this is incompatible with the AMD/ATI proprietary video drivers. The X Server is the display server for Linux. 

Anyone installing 16.04 on a machine with an AMD/ATI video adapter will get by default an open source video driver. Either radeon or amdgpu depending on the video adapter.

Your choice is either to stay on 16.04 and hope things improve by the end of the summer. Or, install 14.04.4 for the time being. A lot of work is being done to make the open source video drivers for AMD/ATI video cards a lot better. User might see some improvement by the end of summer.

See, Known issues - Graphics & Display in the 16.04 release notes.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

A more detailed explanation

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

Installing an AMD/ATI proprietary video driver downloaded from the AMD web site will not work for the reasons given and if our hardware is old the newest drivers from the company web site may have dropped support for the older video adapter. This does happen.

Written by twriter

> For those who don't know, I manage AMD's open source graphics team. We  (AMD) are focusing our Linux graphics driver development on the amdgpu  based open source and upcoming hybrid stacks; consequently, we are not  supporting fglrx on Ubuntu 16.04 LTS. Users who require Pro-graphics or  Workstation class features and performance can continue to use fglrx on  Ubuntu 14.04 until the hybrid stack is available later this year.

[https://www.phoronix.com/forums/forum/phoronix/general-discussion/857070-ubuntu-is-deprecating-fglrx-catalyst-in-16-04-lts/page6](https://www.phoronix.com/forums/forum/phoronix/general-discussion/857070-ubuntu-is-deprecating-fglrx-catalyst-in-16-04-lts/page6)

Regards.

---

### Post by Jan_Corba on 2016-05-12
Thank you. So I will try Ubuntu 14.04.4. and hope that driver will work :)
But, do I need to set ATI radeon as prefered card manualy or Ubuntu will do it aumtomatic (like Windows)?

---

### Post by mastablasta on 2016-05-13
the "old" AMD driver can be install through additional drivers app.


see here for command line install and additional instrutions regarding hybrids: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

after install you need to initialise the display before rebooting 

```
sudo amdconfig --adapter=all --initial
```

Hybrid GPU's are sometimes fully supported, sometimes manual switch and sometimes they are not. depends on the model of laptop.

hopefully AMD will improve the AMDGPU driver fast so users do not have to go thorugh various procedures to get the most out of their chips.

---

### Post by Jan_Corba on 2016-05-15
Hey guys,
I did install proprietary driver by settings/ Software update, but it seem there is still something wrong. Computer is very slow, if I am using graphic program like Darktable. And absolutely wrong is playing flash videos on youtube. It is like I am trying to watch youtube on very old PC- slow, dropping, sound is delayed. Do you thing, is there any way to find righ driver?
A was googling last 4 days and I am really tired.
Thank you for your answers :)

---

### Post by Jan_Corba on 2016-05-15
I have got it confirmed- I turn of proprietary driver for ATI, so now I am using Intel HD graphics and youtube is runing without any problems.
So, is there any chance, that I will get right driver sometime in future?
Or do you think, that I should use other OS?

---

### Post by mastablasta on 2016-05-16
what version of proprietary driver did you install? there is probably some development version and a stable version. you could also try to do manual install - download form amd and then install (just make sure you intiitalise it and check the requirements before trying to install it). 

still the default/suggested driver should work well. does the AMD chip get enough ram assigned (check in BIOS)? what si the output of ```
dmesg
``` command when AMD gpu is enabled? any errors' did you check the error log? i can't remember and my linux pcs are all at home, but does fglrx have a log?

---

### Post by Geoffrey_Arndt on 2016-05-16
Did you actually install 14.04? . . . I'm not clear if you did.   But if you want good graphic performance, get another machine with either nVidia graphics or one of the _newer higher end **Intel** graphics chipsets_.    The Intel graphics machines do not require a special step to install the graphics capability.   Since they are "open source" - - they just run without all the problems and hassles of AMD/ATI.

---

### Post by mastablasta on 2016-05-16
> **Geoffrey_Arndt said:**
>    Since they are "open source" - - they just run without all the problems and hassles of AMD/ATI.
so are the AMD since 16.04 - only opensource

---

