---
title: "Ubuntu 10.10 start up problem"
date: 2010-12-28
forum: Philippine Team
---

### Post by Webster12 on 2010-12-28
Hi Guys, 
 
I recently switched to Ubuntu. Yesterday I was finally able to DL, install, use and update the 10.10, I have restarted and everything seemed fine yesterday pero nung in-open ko sya this morning it won't log me in then I restarted tas puro codes na lang yung lumalabas...said something about GRUB 1.98
 
So meron kayang service center or shop na nag aayos na pwede kong dalhin yung laptop ko. Or if meron diyang marunong pwede pong pa help...
 
Salamat ng madami!!!!!

---

### Post by amsterdamharu on 2010-12-28
The easiest is start from a live CD/USB (Ubuntu CD with option "try Ubuntu without installing" Boot from the CD/USB and run the boot info script (I can't access google right now but it's the first hit looking for "boot info script"). Please post the output of the script here.
When pasting it here please wrap it in &#91;code] &#91;/code] tags.

If you don't have any then you can try the following:
Do you see this?
```
grub>|
```
Then try the following:
Type the following commands (replace 0,7 with the values you got from the first command) In this I use root=/dev/[COLOR=Red]sda3[/COLOR] that is where Ubuntu was installed. I am just guessing here you can try 1 through 12, the wrong one gives you a kernel panic so you have to retry another one like /dev/sda4 or 2:
```
insmod ext2
set root='(hd0,7)'
linux /boot/vmlinuz(press tab to autocomplete or get a list) root=/dev/[COLOR=Red]sda3[/COLOR]
initrd /boot/initrd(press tab, make sure the initrd has the same version number as vmlinuz)
boot
```When you're booted in Ubuntu you have to re install grub and update the grub menu but we need the output of the boot info script to advice you on how to do that.

---

### Post by Webster12 on 2010-12-28
I was actually advised in the Absolute Beginners, the same. The live CD takes forever to load in the TRY UBUNTU section, I am not sure why....unfortunately I do not have enough time to wait because I've really no time but would have on the 30th, I am planning to do that on that day. 
 
As for the second option, yes I can see it but this is what I had:
 
GNU GRUB VERSION 1.98+20100804-5UBUNTU3
 
*IN BOX*
UBUNTU, W/ LINUX 2.6.35-24-GENERIC
UBUNTU, W/ LINUX 2.6.35-24-GENERIC (RECOVERY MODE)
UBUNTU, W/ LINUX 2.6.35-22-GENERIC
UBUNTU, W/ LINUX 2.6.35-22-GENERIC (RECOVERY MODE)
mEMORY TEST (MEMTEST86+)
MEMORY TEST (MEMTEST86+, SERIAL CONSOLE 115200)
 
USE *UP* AND *DOWN* KEYS TO SELECT WHICH ENTRY IS HIGHLIGHTED.
PRESS ENTER TO BOOT THE SELECTED OS, 'E' TO EDIT THE COMMENDS BEFORE BOOTING OR 'C' FOR A COMMAND LINE.
 
As for your solution, I will try that since I was given something differently.....who knows that might work!
 
Here's the thread: [http://ubuntuforums.org/showthread.php?t=1654063](http://ubuntuforums.org/showthread.php?t=1654063)
 
Thanks I will try the second solution tomorrow, if not I will work on it on the 30th...
 
is there really no center or expert i can send my laptop to? I am worried what i'm doing is more fatal....

---

### Post by amsterdamharu on 2010-12-28
No, I thought you didn't get the menu then you have to manually boot.

Since the menu works we need to know what partition you installed Ubuntu on is it /dev/sda3?

Just like drs said:
[http://ubuntuforums.org/showpost.php?p=10286028&postcount=7](http://ubuntuforums.org/showpost.php?p=10286028&postcount=7)

---

### Post by Webster12 on 2010-12-28
> **amsterdamharu said:**
> No, I thought you didn't get the menu then you have to manually boot.
 
Since the menu works we need to know what partition you installed Ubuntu on is it /dev/sda3?
 
Just like drs said:
[http://ubuntuforums.org/showpost.php?p=10286028&postcount=7](http://ubuntuforums.org/showpost.php?p=10286028&postcount=7)
 
Menu? The one I pasted earlier? manually boot?
 
it's in /dev/sda4......i think i partitioned everything in a sda4... :-S

---

### Post by Webster12 on 2010-12-28
> **amsterdamharu said:**
>  
Just like drs said:
[http://ubuntuforums.org/showpost.php?p=10286028&postcount=7](http://ubuntuforums.org/showpost.php?p=10286028&postcount=7)
 
Yup followed that. But it's asking me for init bin..something like that.
 
So I guess I am just going to try the livecd...if it takes for the try me to get to the desktop...like an hour and it's not showing the desktop....shall I still wait?

---

### Post by amsterdamharu on 2010-12-28
> But it's asking me for init bin

I think that means it's not on sda4 but could mean the disk is corrupt.

If you have a USB, a working computer with Internet I would suggest downloading tinycore and use unetbootin to stick that on a USB and boot your computer with it.

It's very small and boots up very quick. It would be the quickest way to find out what's going on and where your Ubuntu is installed.

Don't know how long you have to wait for the Live CD to boot and if that fails, you can try booting from Live CD while we wait. Then check each sda partition and see what's on it.
The output from
```
sudo fdisk -l
``` 
Or the boot info script (doen't run on tinycore but can check fdisk -l to see what parameters you need to grub boot you into Ubuntu.

---

### Post by Webster12 on 2010-12-28
> **amsterdamharu said:**
> I think that means it's not on sda4 but could mean the disk is corrupt.
 
If you have a USB, a working computer with Internet I would suggest downloading tinycore and use unetbootin to stick that on a USB and boot your computer with it.
 
It's very small and boots up very quick. It would be the quickest way to find out what's going on and where your Ubuntu is installed.
 
Don't know how long you have to wait for the Live CD to boot and if that fails, you can try booting from Live CD while we wait. Then check each sda partition and see what's on it.
The output from
```
sudo fdisk -l
``` 
Or the boot info script (doen't run on tinycore but can check fdisk -l to see what parameters you need to grub boot you into Ubuntu.
 
Goodness.....
 
That's a lot of information in one day! It does not look like newbie-ish...
 
But I will try and figure that out. Thanks much and will advice.

---

### Post by jepong on 2010-12-28
suggestion ko is to reinstall... try mo mag burn ng new installer.

---

### Post by stjohnmedrano on 2010-12-29
did you check the md5sum of the iso?

---

