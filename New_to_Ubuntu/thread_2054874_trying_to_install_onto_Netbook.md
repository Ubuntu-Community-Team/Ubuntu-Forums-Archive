---
title: "trying to install onto Netbook"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by thatbloke on 2012-09-08
Hi there

Im trying to fix an Acer Netbook that has no cd drive with an OS that wasnt working. Tried using an old XP disc but is VERY VERY Slow. maybe not compatable so im trying to install Ubuntu via a flash drive.

What ive done is downloaded the OS onto a flashdrive on a seperate laptop I then tried booting the ACER from the flash drive but im getting the error message..

try (hd0,0): FAT16: No GRLDR
try (hd0.1): invalid or null
try (hd0.2): invalid or null
try (hd0.3): invalid or nul
try (hd1.0): NTFS5: No grldr
try (hd1.1): NTFS5: No grldr
try (hd1.2): NTFS5: No grldr
try (hd1.3): NTFS5: No grldr
Cannot find GRLDR
Press space bar to hold the screen,any other key to boot previous MBR....

Any ideas Chaps ?

---

### Post by mike555 on 2012-09-08
I would recommend Xubuntu or Lubuntu , they are much lighter then Ubuntu ...... also you need to install onto a usb drive using a program that makes it bootable,( like unetbootin ) then while starting the netbook push the key to allow usb booting ( it's F12 on mine ) .

---

### Post by scratman on 2012-09-08
Download the .iso, burn it to disc, and run it as a live CD using the drive you used for the Windows XP disc.  The live CD should run with no problems, if so, just install from the live CD using the icon on the desktop.

---

### Post by thatbloke on 2012-09-08
> **scratman said:**
> Download the .iso, burn it to disc, and run it as a live CD using the drive you used for the Windows XP disc.  The live CD should run with no problems, if so, just install from the live CD using the icon on the desktop.

but the netbook has no cd drive :(

---

### Post by scratman on 2012-09-08
You mentioned that you had tried an old XP disc, use the drive you used for the XP disk.  Failing that, you will need to create a bootable USB drive,instructions [here]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot from that.  You may need to alter the boot order from the BIOS on the machine.

---

### Post by thatbloke on 2012-09-08
Sorry didnt explain properly

What i did was transfer the info off the xp disc onto flashdrive.
This seemed to work as it looked like it was installing....then it didnt.
then tried again and got a result. trouble VERY VERY slow.
looked at Acer site and it appears this Netbook didnt use windows. Cant remember what it was.
Anyhoos i came across this ubuntu and tried it the same way..downloaded it onto flash drive and reset the boot order to the USB where the flash drive is.
That is when i get the error message

---

### Post by thatbloke on 2012-09-08
Thanks for your help gentlemen. Downloaded onto UNetbootin and installed brilliantly !

Mind you this xubuntu has taken half the storage space on the netbook:lolflag:

---

### Post by newb85 on 2012-09-08
> **thatbloke said:**
> Thanks for your help gentlemen. Downloaded onto UNetbootin and installed brilliantly !

Mind you this xubuntu has taken half the storage space on the netbook:lolflag:
In most respects, Xubuntu isn't any lighter than Ubuntu.  

Down the road, you may want to have a look at Peppermint (although right now, you're probably glad just to have a running system).  [www.peppermintos.com]("http://ubuntuforums.org/peppermintos.com")  It's built from Lubuntu (in order to use the lighter LXDE), with elements of Linux Mint (specifically, the package management GUI software) pulled in.  By default, it's set up for a lot of cloud computing, with an easy way to set up Site-Specific-Browsers, but you can install as many traditional desktop applications as you wish.

---

### Post by uzumakifahim on 2012-09-08
You can try lubuntu using the same procedure. I think you'll get better result.

---

### Post by Wim Sturkenboom on 2012-09-08
> **thatbloke said:**
> ...
looked at Acer site and it appears this Netbook didnt use windows. Cant remember what it was.
Probably Linpus.

> **thatbloke said:**
> Mind you this xubuntu has taken half the storage space on the netbook:lolflag:
I guess you have a 8GB SSD in there. Just keep it clean by occasionally running *_sudo apt-get clean_*, don't install too much and use it for what it's intended for.

---

### Post by scratman on 2012-09-09
Other options include the purchasing of a reasonably large SD card, tucking it away in the SD slot, and amending your boot up script so that it sees your SD card as additional storage in your home folder.  Another option would be to buy an iPod hard drive and slot it into the laptop in place of the SSD.

---

