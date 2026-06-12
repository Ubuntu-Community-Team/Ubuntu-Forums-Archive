---
title: "Problems with my Ubuntu USB Install"
date: 2018-01-28
forum: New to Ubuntu
---

### Post by clousewa on 2018-01-28
Hi, I'm new to Ubuntu so I figured I'd start in this thread.  I'm trying to install Ubuntu 16.04.3 via bootable USB but I keep getting "Operating system missing" error.  

I downloaded the iso from the official webpage.  I formatted a 16gb flash drive as FAT32 and installed the ISO using UNetbootin and again with Universal USB installer.  Both times I got the same error when trying to boot.  

My system is:
Motherboard: Foxconn A9DA AM3
RAM: 8 gb (1333 Mhz)
CPU: Athalon II x2 270
60 gb internal SSD

Not sure what else I can do.  Do I need to go find a DVD writer and make a bootable disk instead?

Thanks all for your help.

---

### Post by linuchsan on 2018-01-28
What have you installed prior on the usb stick?

---

### Post by clousewa on 2018-01-28
had just been using it as a general storage device.  I wiped it clean using the command prompt, so it should have been totally fresh?  edit: more specifically: diskpart, selectdisk, clean, create partition primary.

---

### Post by clousewa on 2018-01-28
I think I figured it out.  I tried one of my larger flash drives (64gb) and formatted it in FAT32 using [http://www.ridgecrop.demon.co.uk/index.htm?guiformat.htm](http://www.ridgecrop.demon.co.uk/index.htm?guiformat.htm)

Used unetbootin to mount the iso again and it worked the first time.  

Hope this helps anyone experiencing the same problems

---

### Post by onesixtyfourth on 2018-01-29
I always use the start up disk creator with no issues.

---

### Post by HermanAB on 2018-01-29
Technically, you don't need to format the device before writing the image.  You could simply write the ISO file to a USB thingy with dd or cat and be done with it in no time.

---

