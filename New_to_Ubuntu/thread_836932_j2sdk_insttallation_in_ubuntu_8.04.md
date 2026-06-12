---
title: "j2sdk insttallation in ubuntu 8.04"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Jai Haravu on 2008-06-22
Hi

I recently downloaded and installed Ubuntu Linux 8.04 version (hardy distribution)
1. I downloaded the j2sdk-1_4_2_17-linux-1586.bin from the Sun web site
2. The bin file was converted into a deb file using the Java-package supplied with Ubuntu 8.04
3. I then tried to install the deb file using the Debi Installer from a non-root folder (this is what is advised).
4. I have enabled packages form both Multiverse and Universe from Third Party Sources.

The problem I faced and seen in the terminal window is: Failed to install package sun-j2sdk1.4_1.4.2+17_i586.deb
 xul runner-1.9 conflicts with j2re1.4
   sun-j2sdk1.4 requires j2re and is to be installed
dpkg: error processing /home/jharavu/sun-j2sdk1.4_1.4.2+17_i586.deb (- conflicting packages - not installing j2sdk1.4) 

Any help would be most gratefully acknowledged. 
[http://ubuntuforums.org/images/icons/icon14.gif](http://ubuntuforums.org/images/icons/icon14.gif)
Jai

---

### Post by Qrikko on 2008-06-22
not tested.. but something like this feels like it should do the trick..

```

sudo apt-get install sun-java6-jdk sun-java6-plugin sun-java6-fonts
sudo update-java-alternatives --set java-6-sun

```

maybe it is more then you want.. but well.. I see no reason you would like to not put it while you are at it :P

---

