---
title: "HOW TO: ndiswrapper-1.34 on 32Bit Edgy"
date: 2007-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by phossal on 2007-01-27
Updated through Fiesty and ndiswrapper 1.43

If you visit the web site for ndiswrapper ([http://ndiswrapper.sourceforge.net/joomla/)](http://ndiswrapper.sourceforge.net/joomla/)), you'll find a download link. That link will take you to whatever current stable version exists. Assuming you have a fresh install of Fiesty, you'll need to run:
```
sudo apt-get install build-essential
``` to get the compilers necessary for installing ndiswrapper.

Then download the ndiswrapper tarball, which is something like: ndiswrapper-1.43.tar.gz. Save it to your desktop. Right-click and extract it, which will produce a folder named: ndiswrapper.

CD into the folder:
```
cd ~/Desktop/ndis*
```

Now run the following in order:
```
sudo make uninstall  
sudo make
sudo make install
```

These instructions are made available with the ndiswrapper tarball. I have made no contributions.

---

### Post by phossal on 2007-01-28
Removed

---

### Post by Floppyjoe on 2007-01-31
Works great. Thanx Phossal

---

### Post by phossal on 2007-01-31
Removed

---

### Post by Floppyjoe on 2007-01-31
Do you need to delete and reinstall your ndiswrapper installed drivers after this update?Mine seem to be working without doing that but i did it anyway.

---

### Post by phossal on 2007-01-31
Removed

---

### Post by finferflu on 2007-02-07
Thanks! It seems to work with version 1.37 as well!

```
# ndiswrapper -v
utils version: 1.9
driver version:        1.37
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
```

---

### Post by amish on 2007-02-20
Hi 

Many thanks for your post - helped me out a treat!!

I also found this article helpful - between the two I managed to get my Dlink DWL-G650+ working.

I too installed ndiswrapper-1.37

amish

---

### Post by amish on 2007-02-20
Sorry 

this is the other article!!

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)


and this one was of some use :

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-770cc4fc47d7c99ccc91a405c33a4439793a92f4](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-770cc4fc47d7c99ccc91a405c33a4439793a92f4)


all the best

A

---

### Post by phossal on 2007-02-20
Removed

---

