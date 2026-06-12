---
title: "accessing bios on sony vaio pcg-7a2l"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by alwiap on 2008-05-13
Hello,

I am trying to put Ubuntu on a Sony VAIO pcg-7a2l, and it has XP preinstalled.  What button do I have to press to access the BIOS at startup, there is no indication on the screen anywhere?

Thank you!

---

### Post by alwiap on 2008-05-13
nevermind.. found it at F2.  I wish they told you on the bootup screen.  :)

---

### Post by alwiap on 2008-05-13
Sorry, but I have another problem:

I was able to access the BIOS, and when I went to the boot menu, I didn't have an option to move the 'optical drive' up so it would read, and I didn't see an option for CD-ROM.  In other words, I still can't get the computer to boot from CD. Any ideas? Maybe someone with a VAIO has a solution.  Thanks!

EDIT:  I'm in the BIOS screen right now, should Network Boot be enabled (it is currently disabled).  ?

---

### Post by kerry_s on 2008-05-13
on my vaio you press the "-" sign to move the top boot device down.
no you don't need network boot on.

---

### Post by alwiap on 2008-05-13
> **kerry_s said:**
> on my vaio you press the "-" sign to move the top boot device down.
no you don't need network boot on.

ok, i moved the optical drive to the top and made sure the hard drive was the last thing to boot, and rebooted, but it still went straight to windows without recognizing the cd.  Any ideas? Thanks for your help sofar.

---

### Post by kerry_s on 2008-05-13
did you burn the iso as a image at 4x? you can't just copy it to cd.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by alwiap on 2008-05-13
yep, i burnt it to a cd (i have used the same cd to install ubuntu on another laptop, so it's not a image issue.)

---

### Post by Inxsible on 2008-05-13
> **alwiap said:**
> ok, i moved the optical drive to the top and made sure the hard drive was the last thing to boot, and rebooted, but it still went straight to windows without recognizing the cd.  Any ideas? Thanks for your help sofar.Did you save and THEN exit from the BIOS. Please go into the BIOS and check if the optical drive is listed before the hard disk.

---

### Post by Simeo on 2011-02-11
I'm trying to install Ubuntu 10.10 on a PCG-7A2L as well and I still can't get it to boot to either the CD or flash drive. How did you get this to work??

---

### Post by Quackers on 2011-02-11
Press F2 during boot and your bios screen will appear.
Using the up/down and side arrows go to the "boot" screen.
Use the arrow keys to highlight the cd drive or optical drive then move that entry up to the top of the menu by pressing shift and + together.
The flash drive may be a little more invovled.
If there is a * next to the entry for usb flash, you will need to enable external boot device option on an earlier bios screen (also for usb HDD - as sometimes a flash drive can be recognised as a usb HDD - like on my Vaio) then do the above to move an entry to the top.
Then save the current settings (possibly F10) and reboot.

---

### Post by Simeo on 2011-02-11
Yep, I did this for optical drive. There is no entry for USB flash/drive. 

It's still booting straight to windows... (thank you for the quick reply)

---

### Post by Quackers on 2011-02-11
Is there an entry for external boot devices?

---

### Post by Simeo on 2011-02-11
I see (in this order): Optical Drive, Floppy Disk, Network, Hard Disk

---

### Post by Quackers on 2011-02-11
Does anything happen if you highlight hard disk and press enter?
Is there a previous bios screen (maybe "advanced") where you can choose to enable external devices?

---

### Post by Simeo on 2011-02-11
When I scroll to "Hard Disk Drive" and press enter a drop-down shows up saying "Hitachi_DK23FA-80-(PM)" I'm going to guess that's the model of the installed hard drive. 

I don't see an expanded "Advanced" menu. The only options the advanced menu tab has are "IDE CHANNEL MASTER 80GB, IDE CHANNEL 0 SLAVE CD/DVD", LCD SCREEN EXPANSION:, NETWORK BOOT, SHOW VIAO ANIMATION LOGO, SPEAKER VOLUME, HOTKEY EVENT CODE"

---

### Post by Quackers on 2011-02-11
Maybe your system can't boot from a usb device - some can't.

---

### Post by Simeo on 2011-02-11
but not boot from CD either?? Is there any fix for something like this or way to update the Bios?

---

### Post by Quackers on 2011-02-11
It should boot from the cd drive. 
When booting with the cd in the drive, what happens? Is the disc completely ignored? If so, how did you burn the image to disc?
Did you check the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

