---
title: "Usplash error 6: Segmentation Fault"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by sayakb on 2008-09-21
Yesterday, I just made some minor changes to my system.
1. Removed my swap partition and converted it to reiserfs
2. Installed 4-5 usplash themes to test. I tested them using this script I have:
```
usplash -c $1 &
sleep 1
usplash_write "TEXT Testing usplash theme..."
sleep 2
usplash_write "SUCCESS OK"
usplash_write "TEXT Now gona fail!"
usplash_write "PROGRESS 50"
sleep 2
usplash_write "FAILURE Failed"
usplash_write "TEXT Now the progress is full"
usplash_write "PROGRESS 100"
sleep 2
usplash_write "SUCCESS OK"
usplash_write "TEXT Lets pulsate..."
usplash_write "PULSATE"
sleep 10
usplash_write "SUCCESS OK"
sleep 10
usplash_write "QUIT"
```But now, my boot splash appears, the small bar goes back n forth, and instead of filling up from the left, I have my screen blanked with text. The first line indicated the segmentation fault, error 6.
There are no other errors except for Firestarter which already existed before the problem arose. So now, instead of a graphical splash, I have text. Removing the extra usplash themes that I added and re-formatting the partition as swap didn't help.
I have also tried reinstalling usplash, and also, purging and installing it again (which made me lose my ubuntu-desktop and kubuntu-kde4-desktop metapackages) 
I have checked everything with startup-manager and turned off text during boot. I have checked that I have a **ro quiet splash** in my menu.lst
How do I get my graphical splash back? :(

---

### Post by sayakb on 2008-09-24
Bump.

---

### Post by Delkster on 2008-10-12
This is really a shot in the dark, but I had something similar happen with my system, and I just figured out what was causing it in this case (well, sort of).

I've originally installed the system back in the day when my IDE drives were still recognized as hdX, not sdX as they nowadays are. Most settings had already been updated for the new scheme a long time ago, but there happened to be a leftover "resume=/dev/**h**da5" in GRUB (bootloader) settings in /boot/grub/menu.lst.

The resume parameter is used for determining which swap partition to attempt resuming from when waking up from hibernation. I hadn't really noticed the problem with the setting since I haven't tried hibernating the computer in a long time, but apparently not having the partition around caused usplash to segfault. (Yeah, it surprised me, too.)

Even if reformatting the swap partition didn't help, maybe it's worth a shot taking a look at your grub configuration and perhaps removing the resume option if you don't use it. If you need help doing that, let me know. (I suppose that you're familiar with editing menu.lst since you mentioned it in your post, but this is in Absolute Beginner Talk so I'm assuming nothing.)

Good luck!

---

