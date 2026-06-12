---
title: "Install Custom Live CD on USB Stick"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Djalmahal on 2008-11-03
Hi, I just installed Ubuntu 8.10 and added applications and themes that I Like. Now I made a custom LiveCD Iso-File with remastersys. I now tried to burn this on a USB Stick with the new "Create a USB Startup Disk" Tool, but it doesn't accept the ISO-File, virtualBox runs it fine. How can I get this custom LiveCD on a USB Stick with the ability to save and modify files etc.

Thanks for your input
Andreas

---

### Post by mshipman on 2008-11-03
Pendrivelinux has a great tutorial on how to make a casper-rw persistent USB stick from a live-cd: [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

---

### Post by Djalmahal on 2008-11-04
Alright, I will give this a try, I have to buy a bigger USB Stick though. ALso, I have to try to modify the code  so I don't need a woking CD-Drive, as that is no longer working on my old laptop.

Thanks
Andreas

---

### Post by C.S.Cameron on 2008-11-04
Usb-creator seems a little bit choosy about what iso's it installs.
You might have more luck installing a custom iso using Unetbootin.
It has lots of options.

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent", (this must be done at every boot that you want persistence.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

---

