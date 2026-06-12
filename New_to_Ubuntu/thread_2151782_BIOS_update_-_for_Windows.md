---
title: "BIOS update - for Windows?"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by dvdhudson33 on 2013-06-05
Having some issues with my HP Mini 1001TU since upgrading to Ubuntu 13.04.  See [this thread]("http://ubuntuforums.org/showthread.php?t=2134778&p=12678142#post12678142") for details.

I know that before I file a bug report, I need to update my BIOS.  That's when I came across [this page]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-83458-1&cc=us&dlc=en&docname=c01787583&lc=en&os=2093&product=3838214&sw_lang=") saying the Mini's BIOS update is 'important', but it calls it "**WinFlash for HP NetBook System BIOS - Microsoft Windows-Based**", which sounds kinda Windows-specific.

What do you think?  Should I proceed?  (And if I do, how do I install it, given that it downloads in .exe?  Through Wine?)

Thanks in advance for the help ...

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by dvdhudson33 on 2013-06-05
Yeh, I thought the Wine option would be somewhat crazy.

I'll get to work on dl'ing a Windows ISO.  Thanks, Mr Ahallubuntu (which sounds like a city in India).

---

### Post by mastablasta on 2013-06-06
boot disk should be enough for BIOS update i believe. 
it's been a while since i went with this ricky move but last time i did it i ran in off a floppy. so i guess if you put it on a bootable CD (recovery perhaps?!) it should od it.

---

### Post by Mark Phelps on 2013-06-06
Updating a BIOS, if done incorrectly, is a sure-fire way to turn your PC into an electric brick!  This is NOT like installing drivers or apps.  This carries a very high risk with it.

BEFORE you attempt any BIOS update, to ensure that you still have a working PC after the update, you need the following: (1) a way to save off the existing working BIOS such that it can be restored, and (2) a way to restore the saved BIOS if the update goes badly or the new BIOS version presents problems.

If you don't have both of these, you are asking for trouble doing a BIOS update.

---

### Post by Cheesemill on 2013-06-06
Whenever I've needed to do a BIOS update on a Linux machine I use [UNetBootin]("apt://unetbootin") to create a bootable FreeDOS USB stick.

Most manufacturers will supply their BIOS updates as an .exe file for the flashing tool and a .bin file for the BIOS image, just copy these to your USB stick and boot from it so you can flash the BIOS.

Some motherboards will let you flash the BIOS directly from a boot option, all the recent Giga-Byte mobo's that I've used will let you flash them directly from an image file on a USB stick.

---

### Post by dejavue on 2013-06-06
> **Cheesemill said:**
> Whenever I've needed to do a BIOS update on a Linux machine I use [UNetBootin]("apt://unetbootin") to create a bootable FreeDOS USB stick.

Most manufacturers will supply their BIOS updates as an .exe file for the flashing tool and a .bin file for the BIOS image, just copy these to your USB stick and boot from it so you can flash the BIOS.

Some motherboards will let you flash the BIOS directly from a boot option, all the recent Giga-Byte mobo's that I've used will let you flash them directly from an image file on a USB stick.

Actually most manufacturers nowadays supply the flashing tool integrated into their BIOS (Asus, Gigabyte for example), so you only need to put the BIOS.bin file onto a flash drive and find your upgrade option in the BIOS (i.e. "Asus EZ Flash" - then point to your flash drive and wait).
Modern mainboards check the file integrity first and whether or not the file has the correct BIOS and only when everything checks out will they proceed. Also, many modern MBs have a secondary, back-up BIOS (that can't be erased).

---

