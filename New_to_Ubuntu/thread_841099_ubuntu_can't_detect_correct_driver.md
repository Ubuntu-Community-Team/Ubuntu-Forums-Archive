---
title: "ubuntu can't detect correct driver"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by ilplinux_tester on 2008-06-26
before this i already install ubuntu in my laptop(acer 4520, amd turion 2.0 x2 64bit) but ubuntu can't detect correct display driver so i force the installation with default driver. after finish installation i reboot and failed to enter ubuntu. it stuck at ubuntu loading screen.have some idea? (dual boot installation)

---

### Post by gtdaqua on 2008-06-26
I think its an NVIDIA GeForce 7000M graphics card on Acer 4520. So you have to install the appropriate NVIDIA driver. 

Your driver is not correct and thats why you are not getting the GUI. Press Ctrl+Alt+F1 to login via terminal. Then follow this [guide to install NVIDIA driver]("http://ubuntuforums.org/showthread.php?t=596875"). 

You should have already downloaded the Linux driver NVIDIA GeForce 7000M from NVIDIA's website. Follow the guide to install the required modules. Should be easy.

---

