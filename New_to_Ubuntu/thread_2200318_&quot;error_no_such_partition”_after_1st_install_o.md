---
title: "&quot;error: no such partition” after 1st install of Ubuntu – Boot-Repair doesn’t fix it"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by ian29 on 2014-01-18
Hi – doing first ever install of Ubuntu (13.10) and have no previous knowledge of this or other Linux OS'.  Installing on 11 year old Dell desktop gives the “error: no such partition” error on boot up: -

[LIST]
[*]Intel P4 CPU 2GHz
[*]512MB RAM
[*]HDD A (~60GB, original disk where Windows is installed)
[*]HDD B (~200GB, additional space for media)
[/LIST]
 During installation I was expecting to have the choice of which HDD to install Ubuntu onto however only had the option of HDD B.  Looking through this forum thought that the issue could be related to installing on a big disk ([as per this link]("https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk")).  No difference after following Step 1 (Recommended Boot-Repair) and after following Step 2 (Out-of-disk option) I didn't even get to Grub Rescue – got a blank screen with a flashing cursor at boot up.  Haven’t followed Step 3 (Separate boot partition) yet as thought I’d see if people believe that’s the right approach or not first.
 
Here’s the Boot Info URL after completing Step 1 when still getting the “error: no such partition” error on boot up - [http://paste.ubuntu.com/6769743](http://paste.ubuntu.com/6769743)

---

### Post by DuckHook on 2014-01-18
Hi ian29 and welcome to Ubuntu and the forums,

Your real issue is that your machine is drastically underpowered for Ubuntu. Your specs will not support any of the major-league flavours, especially Ubuntu, which is designed for multi-core CPUs, 2+ GB RAM and modern graphics chipsets. The only flavour with a good chance of working within your HW limits is Lubuntu. Would suggest that you try this most efficient flavour before wasting time chasing down other issues.

---

### Post by ian29 on 2014-01-18
OK thanks for that DuckHook, was under the impression that if I was running XP then Ubuntu would be fine.  So any pointers to removing Ubuntu and moving to Lubuntu from this state please?

---

### Post by DuckHook on 2014-01-18
You don't need to do anything special. Your current state is immaterial to you because it has no data on it that you want to preserve, and your new install should just overwrite the old. Just make sure that you are not installing Lubuntu over your Windows OS and everything should be okay. Make sure you backup all important data, especially that on your Windows drive. Always backup before doing anything important to your system. You should be doing weekly backups anyway, irrespective of changes to the system.

If running XP, please note that it will be dead and buried this coming April.

---

### Post by smuggly on 2014-01-19
Try linux Lite with that box. It works great & comes with a PAE kernel.

---

### Post by ian29 on 2014-01-25
Replaced Ubuntu with lubuntu 13.10 and still in the same state as before (no such partition error).  Latest Boot Repair URL is [http://paste.ubuntu.com/6813195/](http://paste.ubuntu.com/6813195/).  Can someone advise how I can get my PC working again please?

---

### Post by squakie on 2014-01-25
That boot repair output is not showing a drive "b" from what I can see - it shows a single disk (/dev/sda) with multiple partitions, including a linux partition and a swap partition if I am correct.

Perhaps you shoul try booting with the live cd/dvd but instead of selecting "install"  select the "try ubuntu" instead.  This should boot of linux without doing anything to your hard disk(s).  If it does not boot, please note any error messages and/or the state of your display (blinking cursor, text login screen, etc.) and post back here.

If it does boot:

open a terminal window (ctrl/alt/F1) and login using your normal userid and password (the password won't be echoed so it doesn't look like it's going it, but it is).

type:

sudo df -h

then

sudo blkid

Please post the outputs of those back here for us to see.

---

### Post by ian29 on 2014-01-25
[COLOR=#000000]Thanks squakie - screenshots attached[/COLOR]

---

### Post by ian29 on 2014-01-25
and actually looking at that, I guess I partitioned the new disc when I installed it rather than put it alongside the original one as suggested in my original post (sda 1 and sda2)

---

### Post by squakie on 2014-01-25
I'm not sure if you have to mount the disk in order for it to show in either of those when run from the cd/dvd.  While you are booted up that way, can you see your disks in gparted?  Don't do anything to them - just look ;)  I hope that someone who knows this better than me will help you too!

---

### Post by ian29 on 2014-02-02
GParted screenshot attached below

[ATTACH=CONFIG]250035[/ATTACH]```

```

Is there anyone out there with any suggestions on all this please as I'm pretty much at the stage of deleting all partitions and starting a clean install of XP......would really like to sort out a dual boot if I can get some advice though please!

---

