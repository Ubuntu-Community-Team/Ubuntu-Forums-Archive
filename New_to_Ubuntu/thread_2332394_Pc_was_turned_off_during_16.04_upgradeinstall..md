---
title: "Pc was turned off during 16.04 upgrade/install."
date: 2016-07-31
forum: New to Ubuntu
---

### Post by stillstu on 2016-07-31
This laptop is a Presario CQ60 w/AMD Athlon x2 64 chip and 8 gigs of ram. It was running 14.04.4 on its' 250 HDD for a few years now. Just fine. It was a Vista machine.
Durning the upgrade to 16.04.1 it was turned off. Oops, sorry. 
Now it boots somewhat but hangs at; [these num's change] sd 4:0:0:0 [sbd] Asking for cache data failed. Assuming drive cache: write through (stuck in a loop)
I can get to the Gnu Grub ver: 2.02 beta 2-9 ubuntu 1.11 screen and choose any recovery mode to no avail. 
So, I burn a DVD iso image of 14.04 & 16.04.1 (seeing all of its folders) and tried to install it, again, to no avail. Put this DVD in my Windows laptop and it seems to work.
It 'will not boot' from the cd/dvd drive. Why not? Made sure the boot order was correct. I have read several posts looking for the same issue.
Right now this laptop is a Fine paperweight! I have named it FRED, f'in ridicules electronic device. lol
I need some help, please and thank you.

---

### Post by Geoffrey_Arndt on 2016-07-31
Re putting the dvd in your windows laptop, and it seems to work.    What exactly does that mean?    Did it boot up into the Live Ubuntu OS?   

If it did, and the actual dvd image is NOT the issue (in other words, it was created correctly), THEN, you should further investigate how your bios must be setup to boot from external media.   Sometimes "boot order" means nothing . . . because the setting is needing something else than what is showing.   Investigate every single option and page in your bios to find the right combo.   Did you look into your owners manual for instructions.   If you don't have an owners manual, use your windows pc to look up the owners manual online.

Also, it may be helpful to see the bios settings in the windows pc, to see if it is different . . and yes, I understand the bios may be different because of vendor (bios maker).   But still worth a look.

Now, if the dvd DOES NOT boot up into Ubuntu Live OS on the windows pc . . that means it is likely the image was not burned correctly.

Also, have you tried USB Flash-Stick as the boot device?

---

### Post by stillstu on 2016-07-31
Thanks for the reply. Putting the disk in my windows brings up a choice, I choose to run wubi.exe and that brings me to Ubuntu menus, so ya I do not think the DVD is the issue.
As for the Presario's bios / boot. CD-ROM Boot is enabled, Floopy Boot is enabled, Internal Network Adapter Boot is disabled.
The boot order is Internal CD/DVD Rom Drive 1st, USB Diskette Key 2nd, USB Hard Drive 3rd, USB Floopy 4th, Notebook Hard Drive 5th, Network is Last
I only get to rearrange these. I will keep trying every single option. What's a owners manual? If was written for men I'm sure I don't have it. lol
I put the 14.04.1 disk in and fire it up, it starts to load 16.04. but it will fail. Asking for cache data. An end less loop. Asking... Assuming
Doing a Ctrl+Alt+Del brings me to the GNU Grub menu... same as F-11.... Recovery 
I can choose from many recovery options. None work. I can edit or change command lines.
I would like to tell it to look at... to boot from the DVD ROM drive. Not the HDD during recovery. 
Is this possible?
And no I do not have a USB Drive, got lots of DVD-R disks

---

### Post by Geoffrey_Arndt on 2016-08-05
_Are you certain the DVD disk is burned as a "bootable iso image"_ versus just copied files from the download?    Because one can see folders and files on the DVD, that doesn't mean it's working properly or is a bootable image.     Can you use that DVD on another computer (maybe a friends system, or a library PC) to see if it will actually boot from it after a shutdown - restart?   I always burn my iso images at either 4x or 8x speeds versus anything faster.

---

### Post by oldfred on 2016-08-05
You do not boot Ubuntu installer from inside Windows. If you are getting the old wubi, you booted from inside Windows not from BIOS.

So test on other system did not really say if DVD is good or not. 
Can you boot from BIOS it the question.

---

