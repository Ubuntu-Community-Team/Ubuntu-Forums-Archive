---
title: "ubuntu - creating a usb boot image"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-11-03
I have a laptop that i want to put ubuntu on it, 
maybe xbuntu if its not fast enough 512 + 1.4ghz

My problem is in ubuntu 8.10 there is a option to create USB start-up disk, every time I create a image I get grub 17, and cant install
The usb pen is 8gb with nothing else on it
Please can someone tell me what im doing wrong

---

### Post by Duck2006 on 2008-11-03
This may be of help.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Soriano on 2008-11-03
I was experiencing a similar problem. I may be misunderstanding what the point of this "Creat USB Startup Disk" is.

I thought I would be able to use this to start say a netbook running Win Xp into Ubuntu.  When i put this Startup Disk into my laptop and tell it to boot from the USB i get like 12 cryptic letters (not english).  It will sit there until I hit a key and will then just boot into XP.  I have tried making the Startup Disk 3 times.

I'm guessing I am just misunderstanding what this app is meant to do.

---

### Post by snowpine on 2008-11-03
I have had very good results making bootable USB's using Unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Good luck!

---

### Post by Soriano on 2008-11-03
I have made one with unetbootin and it does work quite well.  Thanks for the suggestion though.  I was more curious if anyone has had success with the new built in app that comes with 8.10.  I seem to fail with it every time i try.

---

### Post by C.S.Cameron on 2008-11-03
Have tried dozens of times using usb-creator to install to a 4 gig Kingston, without success.
This is what finally worked:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted casper-rw.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

---

