---
title: "Unable to boot on optiplex GX260"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Dwarfyperson on 2008-08-17
So, I've been trying for a month or two to get various versions of Linux to boot on my older computer. the problem is, they don't boot. The computer is a Dell optiplex GX260 with the latest version of the BIOS (A09). My video card is an Nvidia FX5500, and I have 1.25 gigs of RAM. I know that other people have managed to boot Linux on this model of dell, but for some reason both CD and hard drive based boots freeze up at various points during the boot process. my current situation is to run Linux in virtualbox, but this has obvious problems when using it as my main operating system.

If anyone has a damn clue what's going on, it would be a nice change.

---

### Post by pparks1 on 2008-08-17
Dwarfy,

Can you please tell me what version of Linux you are currently trying?  I assume it's Ubuntu 8.04.

We have quite a number of GX260's at my office...I think with the Nvidia FX520 card and i could give an install whirl when I get into the office on Tuesday.

---

### Post by Dwarfyperson on 2008-08-17
It is in fact Ubuntu 8.04

---

### Post by Dwarfyperson on 2008-08-18
Bump for the most epic form of justice and problem solving. In case it isn't apparent, it's not just ubuntu. debian, suse, none of em work.

---

### Post by wolfen69 on 2008-08-18
have you run a memtest from live cd?

---

### Post by Dwarfyperson on 2008-08-20
Yeah, i have, only ran one pass, but it came up clean.

---

### Post by klein de usa on 2008-09-08
hi
i have a gx260, with a nv 6200 agp card, i had ubuntu 7.10 installed along with xp everything was fine, worked realy good after i got it up running, to get ubuntu 7.10 installed i had to disable the failsafexserver, and manualy edit the xorg file to get the computer to boot, after it booted with the mesa or vesa driver i can't remember witch one i used. i installed the nv driver and sudo dpkg-reconfigure xserver-xorg  in a terminal and it worked!

ubuntu 8.04.01 is a diffrent story, i pulled two 20g hdd's out and put in one  250g for more room, i installed xp and went to install ubuntu 8.04.01 from the live cd, cd boots, cd checks fine, when you try to boot into the desktop  it hangs right after the orange bar fills up. so i tryed the alternate cd and it fails at the same place on reboot after the orange bar fills up. 

my xorg file that ubuntu 8.04.01 generated seems blank like it wasn't finished. i'v tryed editing it woth the mesa and vesa drivers but can't make it work, i have the xorg file from ubuntu 7.10 to use as a guide but still haven't been able to get it to work!

i know this is long but i'm hopeing someone will see this that understands how this works better than me

---

### Post by klein de usa on 2008-09-09
hi 
ok i fixed my dell gx260, it now runs ubuntu8.04.01.

 
installed ubuntu 8.04.01 from the alternate cd,

rebooted and right after the orange bar filled up the screen went black

reboot with the alternate cd and at the menu, select rescue a broken system

start a terminal  and use this code:

```
sudo apt-get install nvidia-glx nvidia-settings
```

you have to find and edit the /etc/gdm/gdm.conf file and find this line in it,

FailsafeXServer=/etc/gdm/failsafeXServer

and change it to look like this
 
#FailsafeXServer=/etc/gdm/failsafeXServer 

if you do not edit this line when you reboot failsafeXServer rewrites your xorg.conf file and you have to start all over 

then you have to find and edit the /etc/x11/xorg.conf file to your computer needs, myself being i had ubuntu 7.10 installed i copyed my ubuntu 7.10 xorg.conf file and over wrote the ubuntu 8.04.01 file 

rebooted the computer and ubuntu 8.04.01 came right up and ran 

anyone that doesn't have an xorg.conf file from ubuntu 7.10 to use i can send you a copy of mine. and maybe it will run or you can edit it, it is very eugly because i had to fight with the FailsafeXServer when i installed ubuntu 7.10 also there is just something about these dells or maybe it is the lcd screens that the FailsafeXServer doesn't like.  

gx260 
nvidia pci card 
Dell 1701FP (Analog) lcd screen

---

### Post by Dwarfyperson on 2009-03-07
Just thought I should come back to this. The issue was that I was using pc3200 ram,  whereas init didn't like that. Booting with pc2100 ram only allowed it to boot. this issue has been fixed as of init 2.86 (intrepid).

---

