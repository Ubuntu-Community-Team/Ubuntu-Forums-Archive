---
title: "Save files to Live USB Drive"
date: 2016-09-22
forum: New to Ubuntu
---

### Post by jamesbrown2 on 2016-09-22
How can I save files to the USB which is running the Live Lubuntu distribution?  It does not show as mounted in PCManFM.  Navigating to where it says that it is mounted (/cdrom) brings up the USB drive, but it appears to be locked.  I can not save documents to it from Leafpad or drag files into it using PCManFM.

---

### Post by yancek on 2016-09-22
A LIVE CD is by definition and design, a read-only filesystem.  You have two options.  One, do it all over and create the Live usb with persistence.  Create a second partition, create a mount point and manually mount the partition to copy data to it.  With the second option, you will need to go through this process each time you boot the usb.

---

### Post by Bucky Ball on 2016-09-23
Easiest thing to do is stick another blank USB in another slot while you're running the Ubuntu live session and save to that.

---

### Post by sudodus on 2016-09-23
If the live drive is *cloned* (for example with the Startup Disk Creator of Lubuntu 16.04 LTS, it does not work to create another partition in the [same] USB drive. Either create a persistent live drive from the beginning using a tool for that purpose, or do like Bucky Ball suggest, save to another USB pendrive.

If you want to create a persistent live drive, I suggest that you try [mkusb](https://help.ubuntu.com/community/mkusb) according to this link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent), or install [Simple persistence](https://help.ubuntu.com/community/mkusb/sp)

---

### Post by jamesbrown2 on 2016-09-23
Thank you.

---

### Post by C.S.Cameron on 2016-09-23
When booted from a flash drive you should be able to save stuff to filesystem/cdrom or computer/cdrom, (depending on version).
If you plan on ever accessing this info on a Windows PC it must be on the first partition.

For more info:
[https://ubuntuforums.org/showthread.php?t=2333286&page=2&p=13530799#post13530799](https://ubuntuforums.org/showthread.php?t=2333286&page=2&p=13530799#post13530799)

---

