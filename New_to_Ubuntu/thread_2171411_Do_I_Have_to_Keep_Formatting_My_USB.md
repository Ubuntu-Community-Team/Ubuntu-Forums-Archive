---
title: "Do I Have to Keep Formatting My USB?"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by toady2 on 2013-08-30
I have a lubuntu iso currently on my 2gb usb ( 1.2 gb left after putting lubuntu) and i want to put a puppy linux iso on it. I'm planning on installing puppy on to my internal hard drive from the usb. I want to have a smooth and efficient install so should i completely format my usb to FAT32 or just delete just that lubuntu partition and put puppy on it? Or does whatever i do even mater?Thanks:)

---

### Post by sudodus on 2013-08-30
It depends which method or tool you used and plan to use to make the USB drive bootable with a linux distro.

If you used and plan to use Clonezilla or the Startup Disk Creator, you need only delete all the files (including any hidden files).

If you clone the iso image with dd, you need not delete anything, but if you want to use another method, you need to make a suitable partition table and file system for that method.

See this link for more details 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

