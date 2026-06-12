---
title: "How to Install 'stuff' for Epson Scanner V500"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by ross4 on 2014-06-15
Sorry for using the word 'stuff' but I wasn't sure what to call what I need to install. I have an Epson Perfection V500 Photo Scanner that I want to connect to my Toshiba Satellite 100 laptop running Xubuntu 14.04. I found a good thread on Ubuntu Forum explaining how to do this with a different distribution of Ubuntu on a different (64 bit) machine. Using what I know about my own machine, I followed that thread's pointer to an Epson site where I could download these items:  core package&data package: iscan_2.29.3-1~usb0.1.ltdl7_i386.deb   iscan plugin package iscan-plugin-gt-x770_2.1.2-1_i386.deb  Then I got to the line in that thread that said “install them” and realized I had no idea how to do that! (That's why this is in on the newbie thread.) I could do with a little help on this, since I don't even know  what to search for (install 'stuff'? install drivers? install package?... in Linux) Cheers, Ross

---

### Post by cigtoxdoc on 2014-06-15
I have the same scanner installed on 12.04.  You can open the packages with gdebi, a program you install through Ubuntu Software Center.

john

---

### Post by ross4 on 2014-06-15
Thank you very much for your help.  Gdebi was already installed. I guess it came with Xubuntu 14.04 as I don't remember installing it myself. After a false start, I was able to get the scanner working, not sure to what extent yet. In case anyone else reads this and has a very similar distro and machine, my notes say the following: First install: iscan-data_1.28.0-2_all.deb  Next install: iscan_2.29.3-1~usb0.1.ltdl7_i386.deb  Finally install: iscan-plugin-gt-x770_2.1.2-1_i386.deb   Hope this is of some use to others. Once again, Thanks, Ross

---

