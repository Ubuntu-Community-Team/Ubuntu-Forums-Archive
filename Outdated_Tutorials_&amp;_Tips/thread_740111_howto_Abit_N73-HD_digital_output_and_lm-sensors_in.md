---
title: "howto: Abit N73-HD digital output and lm-sensors in gutsy gibbon"
date: 2008-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by fettmedbobafett on 2008-03-30
Hi!

I thought I'd share how I got the optical digital output and hardware monitoring for the Abit n73HD motherboard working.

I have basically scoured ubuntuforums to find the information, and when you look at it it's quite simple, you just need the latest version of lm-sensors and alsa-drivers, libs and apps to get it working! hope this helps someone ;)

as usual I take no responsibility whatsoever if you decide to give this a go.

**Soundcard**

well, I followed the guide provided at: [http://ubuntuforums.org/showthread.php?t=408148](http://ubuntuforums.org/showthread.php?t=408148)

to understand it I had to translate it using babelfish, here's what it boils down to:
1. go to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and download the current versions of alsa-driver, alsa-lib and alsa-utils (1.0.16 is what I got)

2. untar them.

3. make sure you have the packages required for compiling the packages:
code: sudo apt-get install linux-headers-`uname -r` build-essential ncurses-dev

substitute `uname -r` with the output you get when running uname -r in the terminal, in my case it's 2.6.22-14-generic

4. compile and install the drivers/utils:
change dir to the alsa-driver, and run these 3 commands:
sudo ./configure
sudo make
sudo make install

then repeat step 4 with the alsa-lib and alsa-utils directory. when that's complete, reboot the system and hopefully you have a working soundcard (HDA Nvidia) with digital optical output :)

I had to unmute the IEC958 in alsamixer in order to get sound, it's default seems to be 'mute'.

**LM-sensors**

1. go to: [http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)
download the latest tarball (I got 3.0.1) and untar it.

2. the thing i missed first time around was that I didn't have all the necessary packages installed to compile it. execute this to install the dependencies that you may be missing:
sudo apt-get install bison gcc flex rrdtool

3. enter the dir for lm-sensors, and compile/install it.
sudo make all
sudo make install

4. run sudo sensors-detect, to see which modules to load; for me it was w83627ehf. there is an option to automatically add the modules to /etc/modules, but i recommend that before you add it to modules, you should try and load it manually to see if it works as expected. execute: sudo modprobe w83627ehf

if it loads correctly you should be able to monitor the sensors for temperature/fan speeds from gnome-sensors-applet.

if it works, add it to /etc/modules (sudo gedit /etc/modules), then it will load at each startup.

Hope this helps, and thanks to Gideon26 for the soundcard guide!

---

