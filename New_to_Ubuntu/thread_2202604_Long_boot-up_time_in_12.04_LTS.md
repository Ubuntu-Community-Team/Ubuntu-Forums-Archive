---
title: "Long boot-up time in 12.04 LTS"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-30
It takes so long to boot up that it's annoying. When I choose Ubuntu 12.04 from the Grub menu, the screen goes blank (kinda purplish) for 3-4 minutes before the desktop appears. What's taking so long?

---

### Post by sudodus on 2014-01-30
Please describe your computer! It makes it possible to give relevant advice.

- Brand name and model
- CPU
- RAM (size)
- graphics chip or card

And please describe the system itself. Is it a standard Ubuntu 12.04 LTS, updated/upgraded to the current state? Have you installed some special software that is started automatically during the boot process?

---

### Post by bc.haynes on 2014-01-30
Computer =  Lenovo M78-5100C2U
RAM =           4 GB
Video Card =    Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7540D]
CPU =            Two core AMD 3.6 GHz

I have done a:
```
sudo apt-get update

sudo apt-get upgrade
```

I don't know of any programs I have downloaded that run in the background or load on boot-up.

I am running plain vanilla Ubuntu 12.04 LTS.

---

### Post by squakie on 2014-01-30
If you have any external USB disk drives, try unplugging those from your computer and see if it helps.  I ran into a similar issue and someone suggested this to me to isolate the problem.  I had to make changes in my BIOS to work it out.

---

### Post by sudodus on 2014-01-30
There could be problems with the graphics driver (for example that it is testing severai settings before deciding which one will work). Have you checked if there is a proprietary driver for the Radeon card? I have not much experience with Radeon cards, so I hope someone with more experience can chip in and help you.

Or there could be problems reading some sectors on the HDD. You can check that after unmounting with ```
sudo -f e2fsck /dev/sdxy
``` where x is the drive letter and y is the partition number (for the root partition).

---

### Post by oldfred on 2014-01-30
You may want to check log files.
First one to review:
 gksudo gedit /var/log/dmesg

For example mounting my files is slow and seems to take awhile.
> [    1.917979] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   22.418242] Adding 3068376k swap on /dev/sda6.  Priority:-1 extents:1 across:3068376k 


Have found that if mounting NTFS partitions, it can be slow. And if too slow a chkdsk from Windows may help.

---

### Post by bc.haynes on 2014-01-30
Thank you, Gentlemen,
I decided to do a clean install of 12.04.3 LTS, and everything is the same. It may be the video card. Mine has problems with newer distros and different distros. I have to use **nomodeset** with them.

---

