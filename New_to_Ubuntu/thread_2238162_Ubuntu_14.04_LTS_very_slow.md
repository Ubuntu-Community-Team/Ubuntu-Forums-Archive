---
title: "Ubuntu 14.04 LTS very slow"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by wannbenixdude on 2014-08-06
I am trying to get setup for a  Linux essentials class I will be taking. I have loaded Ubuntu 14.04 LTS on an old desktop I have. 

Memory 2gig 
Processor Intel Celeron 2.5ghz
Graphics card Intel 865G x86/MMX/SSE2 
OS 32 bit 
Disk 76.5gb  

top shows plenty of memory free but the gui is slllllooooooowwwww ! 

Is there anything I can do other than running a "liter" version. I have Lubuntu loaded on my old laptop but its pretty skinny compared to the full version of Ubuntu. 

Thanks in advance.

---

### Post by JazzPotato on 2014-08-06
Have you installed graphics card drivers? If so, how and which ones?

---

### Post by mastablasta on 2014-08-06
it is slow because you have a bad GPU chip: Graphics card Intel 865G x86/MMX/SSE2

you do not need to install any additional drivers. the default unity desktop uses 3D hardware acceleration to draw windows. so it requires a descent GPU to do that. 

solution - install a desktop that does not need 3D acceleration just to draw windows - have a look at Xubuntu or Lubuntu. 

you can search for package xfce4 in software center and install that to get Xubuntu xfce desktop. have a look: [http://askubuntu.com/questions/223536/how-can-i-install-xfce-along-side-unity](http://askubuntu.com/questions/223536/how-can-i-install-xfce-along-side-unity)

---

### Post by 3rdalbum on 2014-08-06
This is an old tutorial. I don't usually recommend using old tutorials on current Ubuntu versions, but this one won't do any harm:

[http://itsfoss.com/speed-up-ubuntu-unity-on-low-end-system/](http://itsfoss.com/speed-up-ubuntu-unity-on-low-end-system/)

Not sure if it still works (I hope so!), but even if it doesn't it won't break anything.

---

### Post by robin7 on 2014-08-06
I'm running [**Xubuntu**]("http://xubuntu.org") on an old relic with only 1/4th of your computer's resources and it runs fast and nimbly.  No 3D-acceleration needed, and just a little bit of "eye candy" to make it sweeter. I promise you'll love it!

---

### Post by mörgæs on 2014-08-06
For this graphics processor it sometimes helps adding an xorg.conf. More info in the link in my signature.

---

### Post by terrykiwi83 on 2014-08-06
Have you tried preload?

```

sudo apt-get install preload

```

I have always installed preload and notice great improvements. Try it, restart your computer and it should start to be more responsive.

---

### Post by JohnnyComeL8ly on 2014-08-07
I have a P4 @ 2.8 GHz, 1 GB of ram, 20GB HDD and the same graphics chip as OP (all inside a GX270).  I used to try to run Unity, but of course the GUI was laggy.  Do like suggested above, get Lubuntu or Xubuntu.  I have Lubuntu, and yes I miss some things about Unity/Ubuntu, but the GUI isn't that hard to change from and (more/better) performance is definitely worth it.  

  Yes, you could just install the needed packages to get LXDE or XFCE, but I recommend just getting the proper ISO for the job, just my humble opinion, of course.  I recommend this route, because it's really hard to clean up unnecessary packages from your PC (I already tried something similar, but... that's [SIZE=3]**if**[/SIZE] you try to remove Unity because you aren't going to be using it any more).  If you try it out and like it, and want only Lubuntu/Xubuntu... then really, just get the ISO.
;)

---

### Post by robin7 on 2014-08-07
> **JohnnyComeL8ly said:**
> I have a P4 @ 2.8 GHz, 1 GB of ram, 20GB HDD and the same graphics chip as OP (all inside a GX270).  I used to try to run Unity, but of course the GUI was laggy.  Do like suggested above, get Lubuntu or Xubuntu....  I recommend just getting the proper ISO for the job ...  If you try it out and like it, and want only Lubuntu/Xubuntu... then really, just get the ISO.
;)

If you have plenty of room on your hard drive and want to try it out first - installed rather than from a LiveDVD, so it'll be a faster more realistic experience - then you can get Xubuntu and Lubuntu, with all the configurations and settings just as they are in the ISOs using the metapackages:

```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install lubuntu-desktop
```

When installation is finished, you can log out of your Ubuntu session, then choose Xubuntu or Lubuntu for a new session. Drive 'em around, kick the tires, see how you like them!

---

### Post by Rob Sayer on 2014-08-08
> **robin7 said:**
> If you have plenty of room on your hard drive and want to try it out first - installed rather than from a LiveDVD, so it'll be a faster more realistic experience - then you can get Xubuntu and Lubuntu, with all the configurations and settings just as they are in the ISOs using the metapackages:

```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install lubuntu-desktop
```

When installation is finished, you can log out of your Ubuntu session, then choose Xubuntu or Lubuntu for a new session. Drive 'em around, kick the tires, see how you like them!

While I have had multiple DEs installed on my netbook in the past, I would not recommend doing it.  It can really cause problems because they may use different versions of the same library component etc.  This comes from the advice of a number of *seriously* knowledgeable Linux geeks here and elsewhere and they convinced me.

I'd make an exception for installing kubuntu-desktop because it uses the Qt libraries whereas all the others use GTK libraries so there's much less chance of conflict.  But on an older machine like the one the OP uses I'd actually recommend XFCE (xubuntu).  I used lubuntu 13.10 on my 1Gb netbook and was happy with it.  But Lubuntu 14.04 was just so buggy I'm going to wait for a stable release of LX-Qt before trying again.  Maybe lubuntu 14.04.1 is better but I'm not going to bother with it.

---

### Post by Jonathan Precise on 2014-08-10
> **Rob Sayer said:**
> While I have had multiple DEs installed on my netbook in the past, I would not recommend doing it.  It can really cause problems because they may use different versions of the same library component etc.  This comes from the advice of a number of *seriously* knowledgeable Linux geeks here and elsewhere and they convinced me.

+1

[HR][/HR]

> **Rob Sayer said:**
> I'd make an exception for installing kubuntu-desktop because it uses the Qt libraries whereas all the others use GTK libraries so there's much less chance of conflict.

-1: I installed kubuntu-desktop, changed DE, changed back to Unity DE, and the theme looked kde style. I had to fix this by going to kde settings, changing the theme to "GTK Engine", change the gtk theme for kde to the one I was using previously in Unity DE, change the Icon set for kde, and change the cursor from kde's default cursor theme to DMZ-white. I do not recommend changing to kde and switching back to Unity.

---

### Post by JohnnyComeL8ly on 2014-08-23
> **Jonathan Precise said:**
> +1

[HR][/HR]



-1: I installed kubuntu-desktop, changed DE, changed back to Unity DE, and the theme looked kde style. I had to fix this by going to kde settings, changing the theme to "GTK Engine", change the gtk theme for kde to the one I was using previously in Unity DE, change the Icon set for kde, and change the cursor from kde's default cursor theme to DMZ-white. I do not recommend changing to kde and switching back to Unity.

I haven't tried that, but I recommend that people use the unique DE's ISOs because I too have had problems (example: Cinnamon-DE alongside an Ubuntu install -- the icons didn't appear properly in the menu -- and other minors things with other mixes)

If you don't have the space to install each ISO at the same time, then back up your stuff on a flash drive or something similar and install them separately.

I haven't looked into it too much, but I think that others (Mr. Precise among the others), who I agree with based on previous experiences, should be harkened to for the whole thing to work "perfectly" as the DE devs intend.

No offence (the previous is just my opinion formed over time). ):P

---

### Post by Rob Sayer on 2014-08-24
Another good thing about trying kubuntu-desktop in a unity install is that, unlike unity, KDE can be seriously configured for speed.  I've had kubuntu on this 1Gb netbook that also has a badly supported video card.  It was a bit too slow for me ... even using Openbox as a windows manager instead of kwin ... but I'm pretty sure I could get it to run in 2Gb just fine.

---

### Post by JohnnyComeL8ly on 2014-08-27
> Another good thing about trying kubuntu-desktop in a unity install is  that, unlike unity, KDE can be seriously configured for speed.  I've had  kubuntu on this 1Gb netbook that also has a badly supported video card.   It was a bit too slow for me ... even using Openbox as a windows  manager instead of kwin ... but I'm pretty sure I could get it to run in  2Gb just fine.

What would be the advantage in doing that?  I mean, why not install Kubuntu?

---

### Post by mastablasta on 2014-08-28
kubuntu and then netbook plasma.

edit: +low-fat settings package or what it's called nowadays....

should work well on 1 GB RAM

---

### Post by nsync on 2014-08-28
try Xubuntu instead :)

---

### Post by mörgæs on 2014-08-28
Now it's three weeks since we heard from original poster. Thanks for all contributions but we should let the thread rest until he returns.

---

### Post by wannbenixdude on 2014-09-03
Afternoon folks, 

Thanks to all.  I wasnt ignoring your advice, I wanted to get into the class and see what would work for me. 

 Im a life long network guy who is trying to sharpen his Linux skills. Im currently enrolled in a local community college Linux essentials course. In addition/in tandem, Im taking Ucertify LPI Essentials and when I need a "go to" Im using the free LPI edx training. Eventually, Ill grab a few ebay blades and add to my mini rack that now houses a modest Router/switch lab. Much of this essentials class material I already know but figured Id take the formal training .. might catch a few things I didnt know. Glad I decided that because I have actually learned a few things I wasnt aware of. Really waiting for the next semester class admin Ive been doing networking since before it was digital. I guess I should say Im an old guy .. 51, the command line is no stranger to me. 

So. Sometimes there are assignements given that I cant finish in class. .. with work, I often have to get back at it at night. The instructor is using Ubuntu 13.10. It would be helpful to be using the Unity desktop for this reason. 

I have a few machines old and crusty. I do have a new IBM think pad W530 that is setup pretty good as far as resources. Eventually Ill load Virtual Box or Esxi on that Laptop but dont want a. to use it in a learning / Lab capacity b. introduce possible difficulites with virtualization that may throw off my Linux study. So I have the dell Dimensions and my old Dell Inspiron 6000 with :
>  -Inspiron-6000:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370/M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
 

The Dimension has Linux 14.04 LTS loaded right now and the Inspiron has Xubuntu 14.04. I think Im going to reverse that. If I read correctly at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)  the video on my Inspiron is fully supported. 

Xubuntu is ok and once Libreoffice was loaded has everything I need for a home pc. If what I am reading is correct, I can use my Inspiron with Unity. 
Gonna move a few things off the Inspiron and give Linux 14.04 LTS a try but first using the LiveCD method. 

Wish me luck and thanks for all the helpful responses !

---

### Post by mastablasta on 2014-09-04
goog luck. anyway these are just user interfaces - they can all run the programs from the others and all use same commands. which is why people here will often give terminal commands to help.

---

### Post by JohnnyComeL8ly on 2014-09-06
I do wish you an easy time of it. :p

---

