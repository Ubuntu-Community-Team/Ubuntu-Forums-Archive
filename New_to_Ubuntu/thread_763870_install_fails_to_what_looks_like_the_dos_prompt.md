---
title: "install fails to what looks like the dos prompt"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by princessaurora on 2008-04-23
hi there guys and girls
I'm trying to install ubuntu to my laptop that is just now running Linux mint
but when booting for the live cd i get the loading bar that fills up as it loads then pop black screen and what look's like the dos prompt

i've tried booting in save graphics mode, both set's of cd's, there are no errors that i can see. 
That's why i installed lime just to see if i was able to get Linux on the laptop at all and that works (using lime to type this). I have ubuntu on my desktop pc so would like the same on both

please help thanks this is doing my head in (been trying for days now):(

intel celeron 1.6 ghz
512 Mb of ram
intel 940gml graphics card (on board)
azalia sound card
40gb s-ata hard disk

---

### Post by Thelasko on 2008-04-23
First try typing```
startx
```
If that doesn't work type ```
sudo dpkg-reconfigure xserver-xorg
```and follow the instructions.

---

### Post by princessaurora on 2008-04-23
tried the above got
startx
/bin/sh: startx: not found
(initramfs)

sudo dpkg-reconfigure xserver-xorg
/bin/sh: sudo: not found
(initramfs)

---

### Post by philinux on 2008-04-23
When you boot the live cd choose the option "check cd for defects".

---

### Post by princessaurora on 2008-04-23
laptop just ends up back the prompt 

busybox v1.1.3 (debian 1:1.1.3-5ubuntu7) built-in shell (ash)
enter help for list of built-in commands

(initramfs)

used this cd for install on desktop

---

### Post by nobles on 2008-04-23
There is a bug in the Intel Xorg driver that seems to be affecting a lot of notebooks with integrated Intel graphics chipsets. I have had problems with four different models of notebooks with Intel Graphics chipsets with the latest Xubuntu Hardy Heron LiveCD - on one I get a flashing dash in the upper left corner, another boots up with a blank screen and two others boot up OK but hang on shutdown and all seem to be related to the Intel Xorg driver.  From what I have found recent Debian distributions have the same problem.  It looks like the bug reports have been made and it is being worked on but there is no good solution yet.  It is kind of disappointing that a bug that affects the use of the new Ubuntu release on so many notebooks wasn't found before this major release.

---

### Post by lswest on 2008-04-23
Have you tried booting it in safe graphics mode?  If so, have a look at the alternate CD, maybe try installing it with that.  Also, it's not a "dos prompt" it's the linux terminal, just so you know the right terminology ;)

---

### Post by princessaurora on 2008-04-23
just waiting for the alt cd to down load again.


> lswest  	
 Also, it's not a "dos prompt" it's the linux terminal, just so you know the right terminology 

thanks for that least i know what it is now :)

---

### Post by princessaurora on 2008-04-23
thanks for the help all up and running now :KS

---

### Post by lswest on 2008-04-23
great, glad it works :)  and yeah, the right terminology always makes questions easier to ask ^^

---

### Post by bharadwaj on 2008-04-23
For a system spec like yours I'de recommend an alternate Disc.

---

