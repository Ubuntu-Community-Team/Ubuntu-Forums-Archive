---
title: "Fix flash problems in 64-bit"
date: 2009-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by undecim on 2009-11-25
I had been having some problems with flash in 64 bit Karmic. Whenever I clicked, there would be about a 9/10 chance that flash wouldn't detect it. 

To fix this, I installed flash from the files at adobe.com. Since I couldn't find a 64-bit flash player debian package at adobe.com, I downloaded Adobe's 32-bit .deb and replaced the libflashplayer.so inside of it with Adobe's 64-bit libflashplayer.so, and modified the package control info, giving me a 64-bit version of adobe-flashplayer (and also my first ever debian package)

Here are the instructions to do it:

First, download and extract the 32-bit package and 64-bit libflashplayer.so:
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
dpkg -x install_flash_player_10_linux.deb install_flash_player_10_linux
dpkg -e install_flash_player_10_linux.deb install_flash_player_10_linux/DEBIAN/
tar -xzf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz -C install_flash_player_10_linux/usr/lib/adobe-flashplugin/

```that will extract each file to its necessary directory, including overwriting the 32-bit flash player with the 64-bit.

Next, edit the control file.
```
nano install_flash_player_10_linux/DEBIAN/control
```Now, change the architecture to amd64, and add flashplugin-installer to the replace list

Change```
Architecture: i386
```to become```
Architecture: amd64
```and change```
Replaces: flashplugin (<< 6)
```to become```
Replaces: flashplugin (<< 6), flashplugin-installer
```Now, update the md5sum for libflashplayer.so```
nano install_flash_player_10_linux/DEBIAN/md5sums
```Change```
d4a8e246003d273cc6093fbaa5da6b10  usr/lib/adobe-flashplugin/libflashplayer.so
```to become```
9903881108ff7cd954a3adf0d00185d3  usr/lib/adobe-flashplugin/libflashplayer.so
```Build the new package```
dpkg -b install_flash_player_10_linux
```And finally, install it```
sudo dpkg -i install_flash_player_10_linux.deb
```

---

