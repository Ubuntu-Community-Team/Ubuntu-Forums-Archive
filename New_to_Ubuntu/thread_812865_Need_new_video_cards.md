---
title: "Need new video cards"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by RWells on 2008-05-30
Hope someone can help me with this a little.
I need to buy three video cards

I have been trying to install Ubuntu 8.04 since the lts release, with no luck.
I cant seem to get it to play nice with my video cards so Im going to give up and start replacing hardware.:(

I have three computers, all with AMD sempron 2200 cpu 
and NVIDIA geforce mx4000 pci video cards.

Can anyone recomend a video card that will work for sure, preferably under $250

Thanks

---

### Post by quelx on 2008-05-30
The cards you have should work fine (using **nvidia-glx-legacy**)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Can you post what is not working and what you have tried thus far?

---

### Post by RWells on 2008-05-30
> **quelx said:**
> The cards you have should work fine (using **nvidia-glx-legacy**)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Can you post what is not working and what you have tried thus far?

Whats not working.

After install Ubuntu boots to a black screen with no command prompt.
ctrl+alt+f2 does nothing.
Only way I can get anything is to select recovery mode and root shell from grub menu

After booting in recovery mode I just start editting xorg.conf and rebooting, at some point I guess ubuntu or xserver gets confused, or mad at me for being so stupid, and boots in failsafe mode and I have gui.


After reaching this point, I have read nearly every post on these forums that have the word NVIDIA in them and tried everything I have read.

At some point I thought I had One of the machines working, I had compiz-fusion with the cube and everything seemed fine, then after one of the recent updates it rebooted to the black screen and nothing I have tried since has panned out.

I have a fourth machine with the same hardware,with Ubuntu 8.04 server and ubuntu desktop installed and to get on here I  plug one of my monitors in to the server.

---

### Post by quelx on 2008-05-30
in safe mode have you run **dpkg-reconfigure -phigh xserver-xorg** ?

have you tried replacing

```
         Driver      "nvidia"
``` with
```
         Driver      "vesa"
```?

have you tried **nvidia-settings** from a working X session?

---

### Post by RWells on 2008-05-30
> **quelx said:**
> in safe mode have you run **dpkg-reconfigure -phigh xserver-xorg** ?

Yes I have tried this ,would you mind explaining what this is suposed to do?

When I run dpkg-reconfigure -phigh xserver-xorg it it only gives the option to reconfigure my keyboard, doesnt offer any thing for video drivers or monitor, and then it replaces the xorg.conf file with a new one that causes the boot to black screen


> **quelx said:**
> 
have you tried replacing

```
         Driver      "nvidia"
``` with
```
         Driver      "vesa"
```?

have you tried **nvidia-settings** from a working X session?

Yes I have edited the xorg.conf file which is the only way I can the saifemode gui, then it generates a warning that says I need to use 

 dpkg-reconfigure -phigh xserver-xorg

Which removes the nvidia driver and then boots to a black screen with no command prompt


nvidia-settings says Idont have any nvidia x drivers and that I should run 
nvidia-xconfig as root, which does nothing,

---

### Post by ardvark71 on 2008-05-30
Hi...

Just as a "try if nothing else works" suggestion...;)

If you have an available computer to burn a CD, you could try 7.10 (Gutsy Gibbon) to see if that performs any better:

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

I've been getting the impression that 8.04 is still needing time to get the bugs worked out.

Best Regards...

---

### Post by RWells on 2008-05-30
> **ardvark71 said:**
> Hi...

Just as a "try if nothing else works" suggestion...;)

If you have an available computer to burn a CD, you could try 7.10 (Gutsy Gibbon) to see if that performs any better:

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

I've been getting the impression that 8.04 is still needing time to get the bugs worked out.

Best Regards...

I have tried 7.10, before I had similar problems with it, but I could edit xorg.conf and get it to use the nvidia driver, but I didnt try using any 3d such as compiz-fusion cube.

---

