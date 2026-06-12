---
title: "GTX 580 - GPU is &quot;locked up&quot; and can't use the higher resolution, only nomodeset"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by BurningCa007 on 2012-10-19
I'm new to Ubuntu in general and I'm very sorry if I posted this in the wrong place, I need some serious help

Judging by the title you can guess I'm not exactly a beginner but the truth is that I've only read up a little and can't seem to find a solution to this problem I'm having.

My system specs:
Motherboard: Gigabyte X58A-UD3R
GFX CARD: Point of View GTX 580
RAM: 6gb triple channel
Processor: i7 930 @2.8 ghz

My problem is as follows: I partitioned my main hard drive to run ubuntu and whenever I try to just launch ubuntu from GRUB I think (the boot menu) I get the login screen and then it hangs and shows me in a console menu that my gpu is locked and it's attempting to switch but to no avail. This goes on in a loop until my computer hangs and I have to restart.

I've tried all the various Nvidia drivers: nouveau, nvidia-common, nvidia-current, nvidia-current-latest via sudo apt-get install (driver). But on some of these I get a blank screen when normally booting in ( i can see the wallpaper just no icons) and the screen is not of a full resolution.

I am using the 64bit version and the only way I can see the icons at a low res is using the nomodeset line when editing the launch option in the boot menu.

All your help is highly appreciated!

Edit: I am using Ubuntu 12.10

---

### Post by BurningCa007 on 2012-10-20
This solved my problem: [https://www.benjaminwiedmann.net/fix-nouveau-driver-issues-on-ubuntu-12-04-install-nvidia-drivers.html](https://www.benjaminwiedmann.net/fix-nouveau-driver-issues-on-ubuntu-12-04-install-nvidia-drivers.html)

These commands:
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get install linux-headers-`uname -r`
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo update-alternatives --config gl_conf
sudo ldconfig
sudo update-initramfs -u
sudo nvidia-xconfig

Idk what they did but somehow I can now run Ubuntu at full res and the icons show up!

---

