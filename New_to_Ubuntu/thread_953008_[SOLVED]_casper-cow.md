---
title: "[SOLVED] casper-cow"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by theozzlives on 2008-10-19
I'm trying to get my mom turned on to Ubuntu. I read in Ubuntu Hacks  that if you format a USB Stick (I'm using a small 128 MB) and label it casper-cow, then select other options and type persistent at the menu on the live CD, the memory stick will save your settings. THIS DON'T WORK help please

---

### Post by t0p on 2008-10-19
You want a persistent live install on a usb stick, right?  Follow [these instructions]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/").

---

### Post by theozzlives on 2008-10-19
> **t0p said:**
> You want a persistent live install on a usb stick, right?  Follow [these instructions]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/").

I'm not looking to install, just save settings & docs, etc

---

### Post by C.S.Cameron on 2008-10-19
I understand the persistence mode on 8.04.1 Live CD is broken.
If you are booting 8.04.1 from flash drive, a method to fix casper is here:
[http://www.pendrivelinux.com/2008/05/23/how-to-fix-ubuntu-804-casper-script-for-persistence/](http://www.pendrivelinux.com/2008/05/23/how-to-fix-ubuntu-804-casper-script-for-persistence/)
Persistence can be enabled this way on a flash drive created using liveusb, Persistence for settings and documents is saved to partitions named casper-rw and home-rw.
I'm not sure how to get things to work if these partitions are on a second disk.
I understand casper is fixed in 8.10 and should work as you describe with the Live CD.

---

### Post by theozzlives on 2008-10-20
Still not doing something right cause it don't work. I've tried 7.10, 8.04, and 8.10 beta. I want my mom to try Ubuntu not Knoppix.

---

### Post by theozzlives on 2008-10-21
IT WORKS!!! I formatted my flash drive with 2 ext3 partitions, then I typed "sudo e2label /dev/sdb1 casper-rw" did the same for sdb2 except "home-rw". Be sure to do "sudo fdisk -l" to be sure of the flash drive.
  I booted with 8.10 beta and hit F6, typed a space and "persistent", then enter. I went to the terminal, typed "sudo su" then "chmod ubuntu /dev/sdb1" same for sdb2.
  It saved all my settings, just do the persistent thing when you boot.
  Anyhow thanks for everyones help.

The Almighty Ozz!

---

### Post by C.S.Cameron on 2008-10-21
Which version ended up working?

---

### Post by theozzlives on 2008-10-22
> **C.S.Cameron said:**
> Which version ended up working?

8.10 Bbeta

---

### Post by C.S.Cameron on 2008-10-22
Thanks again, I got the daily-build of 8.10 working ok, at least persistent home,
Right now I'm trying to figure out if casper is persistent.
Casper-rw partition seems to be filling up, but downloaded applications, (abiword), do not seem to be there after reboot.

Fixed, The casper-rw partition was showing up on my desktop. 
I un-mounted it, now everything seems to be persistent.

---

### Post by theozzlives on 2008-10-23
> **C.S.Cameron said:**
> Thanks again, I got the daily-build of 8.10 working ok, at least persistent home,
Right now I'm trying to figure out if casper is persistent.
Casper-rw partition seems to be filling up, but downloaded applications, (abiword), do not seem to be there after reboot.

Fixed, The casper-rw partition was showing up on my desktop. 
I un-mounted it, now everything seems to be persistent.

Kewl, I was wondering about that.

---

### Post by C.S.Cameron on 2008-10-24
Found that this casper/home USB also works great with Live USB.

---

### Post by mcurran on 2008-11-14
Cameron:  You're a tool.  Why not just mount and copy the iso to a 700MB FAT16 partition on the USB and then create your two ext2 partitions for it to be persistent - just like the tutorials explain?  Then you wouldn't have to even bother with the disk.

What I find lame, is that nobody likes to write-up tutorials for the whole process, you've got to find bits and pieces everywhere and then combine them yourself (kinda like looking for guitar tabs that sound right).

I'm going to write up a HowTo in the LinuxMint forum in a bit, so that it'll be one big smooth process for anyone with Ubuntu or Mint.  Pendrivelinux, particularly the two people just provided to you, give basically all the info. you need.

---

### Post by theozzlives on 2008-11-15
> **mcurran said:**
> Cameron:  You're a tool.  Why not just mount and copy the iso to a 700MB FAT16 partition on the USB and then create your two ext2 partitions for it to be persistent - just like the tutorials explain?  Then you wouldn't have to even bother with the disk.

What I find lame, is that nobody likes to write-up tutorials for the whole process, you've got to find bits and pieces everywhere and then combine them yourself (kinda like looking for guitar tabs that sound right).

I'm going to write up a HowTo in the LinuxMint forum in a bit, so that it'll be one big smooth process for anyone with Ubuntu or Mint.  Pendrivelinux, particularly the two people just provided to you, give basically all the info. you need.

if you read the top of the thread, I was finding a way to turn my mom on to Ubuntu with a 128 MB flash drive, I'm not just gonna give up a big flash drive so she can try the sodoku on it.

---

