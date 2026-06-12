---
title: "How Do I Repair A Corrupted MBR?"
date: 2015-05-26
forum: New to Ubuntu
---

### Post by tb75252 on 2015-05-26
I am using Ubuntu 14.04 LTS, 64-bit.

Last night there was a power surge that might have corrupted my MBR...

Today, when I boot up my desktop PC, I see the following error message:  > No bootable device - insert boot disk and press any key.
If I boot up using GParted Live I get:  > Invalid partition table - recursive partition on /dev/sr0

So, how do I fix this MBR problem?  (Please note that I am a noob.  I will need the easiest way to fix this...)
**Please note that the desktop only has Linux installed --no Microsoft Windows OS is present!**

---

### Post by Vladlenin5000 on 2015-05-26
Try booting with a Ubuntu DVD or USB, then open GParted. 
In GParted find (or try to find) the drive where Ubuntu is installed. Is it showing like it should be?

---

### Post by tb75252 on 2015-05-26
> **Vladlenin5000 said:**
> Try booting with a Ubuntu DVD or USB, then open GParted. 
In GParted find (or try to find) the drive where Ubuntu is installed. Is it showing like it should be?
It does not seem to be able to see /dev/sda.  It only sees /dev/sr0 (which I imagine is the DVD...)

---

### Post by mastablasta on 2015-05-26
try with this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

if not post the output of the script.

---

### Post by Vladlenin5000 on 2015-05-26
I agree with the previous suggestion, it may give some important information.
However, based on the results so far, it isn't looking good. you probably have a bigger problem than just MBR.

---

### Post by tristan16 on 2015-05-26
I had something similar a few days ago where my BIOS couldn't find my main hard drive, as if it wasn't connected. Boot repair on a live USB allowed me to boot once, but then had the same issue every restart. I finally fixed my problem by turning the system off, unplugging the main hard drive (data and power), and plugging it back in. Not sure if this would work with your problem, but it might be worth a try.

---

### Post by leunam12 on 2015-05-26
I wouldn't mind the recursive partition on sr0 error since that is your optical drive but the fact that you can't see /dev/sda looks ugly.
Can you see /dev/sda if you type lsblk at the terminal? Your disk may be bad if you can't see it or if only "/dev/sda" shows up without any numbers. Have you backed up your data recently?

---

### Post by stalkingwolf on 2015-05-26
unfortunately it doesnt look like there will be any easy fix.  I have had some success  with unplugging the computer for a couple hours then trying again.   Might also try running the hdd regenerator on the hirens disk.    I have also had some success with unplugging the power codr and then removing the cmos battery for a couple hours.

---

