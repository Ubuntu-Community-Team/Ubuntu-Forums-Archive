---
title: "how to run.exe program to flash new bios"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by boogar on 2008-06-10
Thats pretty much it I need to update my bios and it requires a .exe program to do it any suggestions?

---

### Post by lazyart on 2008-06-10
BIOS flash is usually done in a dos mode of some sort, though some systems can boot from a floppy/cd/flash drive and update the system bios with the appropriate key press.

What motherboard/computer do you have?  Do you have link to the file or instructions for flashing?

---

### Post by bpl07 on 2008-06-10
> **boogar said:**
> Thats pretty much it I need to update my bios and it requires a .exe program to do it any suggestions?

I do my BIOS flashes with my XP partition.  I'm kinda scared to try it in ubuntu.

---

### Post by unutbu on 2008-06-10
Here is a guide on how to flash BIOS on a GNU/Linux machine if you don't have windows or even a floppy drive:

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

HTH.

---

### Post by tamoneya on 2008-06-10
BIOSes originally we always flashed by booting from a floppy disk.  In order to make things easier manufactures have created other ways to do this.  They make programs (exes) that allow you to flash from within the OS.  They have also allowed you to use USB instead of floppies due to their rarity.  
Personally I strongly recommend that you use a USB drive.  It is a fairly simple matter.  I have tried the exe method and I am 0 for 1 and I will never try it again since a failed BIOS flash will brick your motherboard.  What is your motherboard model.  We can get you directions for using a USB drive.

---

### Post by iaculallad on 2008-06-10
Do it with [Linux]("http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html").

---

### Post by ctc on 2008-06-10
My Gigabyte motherboard has a flash utility installed on the onboard chip. To flash the BIOS, I only needed to put the latest BIOS on a USB device and run the utility from the ROM chip. The problem is the way Gigabyte has packaged the BIOS update. Instead of providing a tar, zip, or direct download, they provide only a self-extracting exe container that contains the needed file. I've had to use a Windows system to actually get the BIOS update onto a USB storage device. I don't know if there's any way around this. It didn't seem like that previous link addressed this particular situation.

---

### Post by Rhubarb on 2008-06-10
ctc:  I use wine / cabextract to extract the BIOS images from an exe (wine will not allow you to flash your BIOS).

Then I use freedos to do the actual BIOS flashing (your BIOS flasher allows you to use DOS to flash - some are windows only):
[HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

But certainly if you can use a USB drive to do it with your motherboards built in BIOS updating utility, use that.

The worst case is that you actually need windows installed to update your BIOS.

---

### Post by ctc on 2008-06-11
Rhubarb: Great. Wine/cabextract was the missing piece that I needed. Thanks.

---

