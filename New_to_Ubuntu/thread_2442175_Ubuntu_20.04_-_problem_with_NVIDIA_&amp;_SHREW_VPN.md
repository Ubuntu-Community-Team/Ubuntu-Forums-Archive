---
title: "Ubuntu 20.04 - problem with NVIDIA &amp; SHREW VPN Client"
date: 2020-04-30
forum: New to Ubuntu
---

### Post by roby.bob on 2020-04-30
Notebook HP8730W dual boot Windows 7 prof. and Ubuntu (two different HD).
NVIDIA Quadro FX2700M FHD G94GLM Video Card.

I updated Ubuntu 18.04 LTS to 20.04 LTS and I have two problems:
[LIST=1]
[*]**I can't manage the NVIDIA card with the original drivers (NVIDIA-Linux-x86_64-340.108.run).** The notebook freezes after a few minutes. With the Xorg Nouveau driver it works but I can't get it to go in FULL HD 1920x1080 (not even with "*xrandr --addmode default 1920x1080_60.00*") 
[*]**Shrew VPN Client** is gone and I can't compile it because Ubuntu 20.04 doesn't allow to install qt4 (*sudo apt install qt4-default*) but only qt5 (*sudo apt install qt5-default*). Could CmakeLists.txt be modified to solve the Shrew VPN problem? How ? 
[/LIST]

Can anyone help me ?
Thanks
Bob

---

### Post by CelticWarrior on 2020-04-30
It's generally a bad idea to use the installer from Nvidia. You have the same drivers already packaged for Ubuntu in the official repository.
So, if you already uninstalled it, I suggest opening Additional Drivers and install from there.
For the second problem I suggest you find a different software.

---

### Post by roby.bob on 2020-04-30
Thanks for your suggestions
For the VPN I need a program that allows PSK + XAuth and I have not found anything similar to Shrew

---

### Post by roby.bob on 2020-05-01
[SOLVED] NVIDIA issue resolved as follows:
cd /etc/modprobe.d
sudo rm nvidia-installer-disable-nouveau.conf
This configuration, created in the manual installation phase of the NVIDIA driver, was partially blocking the Xorg Nouveau driver making it unstable

[NOT SOLVED] The problem of SHREW compilation described above in the first post remains to be solved.

---------------------
 I found the PATCH for Shrew VPN which should solve the QT5 build  problem.
 I am not expert in compiling Ubuntu sources ... I made the various  changes to the files as described here (deleted - red and added +  green): 
[URL="https://github.com/Spectere/spectere-overlay/blob/a21c81a88e64cfb59817861e5e18900b33756a07/net-misc/ike/files/ike-2.2.1-qt5.patch"]https://github.com/Spectere/spectere-overlay/blob/a21c81a88e64cfb59817861e5e18900b33756a07/net-misc/ike/files/ike-2.2.1-qt5.patch
[/URL]
  But the compilation gives me 2 errors. I didn't understand what these other files are for ... maybe managing these could overcome the problem:
 [URL="https://github.com/Spectere/spectere-overlay/tree/a21c81a88e64cfb59817861e5e18900b33756a07/net-misc/ike"]https://github.com/Spectere/spectere-overlay/tree/a21c81a88e64cfb59817861e5e18900b33756a07/net-misc/ike
[/URL]
  Can any expert help us ?
Thanks,
Bob

2 ERRORS:
  682 |    EVP_CIPHER_CTX ctx_cipher;       |                   ^~~~~~~~~~

  make[2]: *** [source/libike/CMakeFiles/ss_ike.dir/build.make:102: source/libike/CMakeFiles/ss_ike.dir/manager.file.o] Error 1
  make[1]: *** [CMakeFiles/Makefile2:375: source/libike/CMakeFiles/ss_ike.dir/all] Error 2 make: *** [Makefile:130: all] Error 2

---

