---
title: "Graphic card driver/configuration (Ubuntu LTS 12.04, Radeon HD 6550M)"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by Veronika_87 on 2014-03-03
Hi all, 
I am quite new to Ubuntu and to this forum. I hope to find help here for my problem:

I have an Acer Aspire 4820TG with two graphic cards one is AMD Radeon HD 6550M and an integrated one Intel(R) HD Graphics. I have Ubuntu LTS 12.04 and Windows 7, so while in Windows I can switch between those graphic cards, as Radeon causes overheating (I use the integrated one), in Ubuntu I could not install AMD Catalyst. Even worse, when I tried to install it did not install properly and after reboot the ubuntu desktop does not load. 

* I uninstalled everything, also fglrx and xserver-xorg, and reinstalled libgl1-mesa-glx, libgl1-mesa-dri and xserver-xorg-core:
  it results in a loading desktop but I can just use keyboard

* then I tried again to install Catalyst with help from this site: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) 

result: Everything was installed properly, but after last reboot I got the warning that 'System is running in low-graphics. 

* resetting the xserver-xorg, reinstalling libg1, leads to the problem that I just can use keyboard. 

-Does someone know how to get the graphic card configuration right?

-Or how I can get at least the configuration that I had after the installation of ubuntu, without reinstalling it?

Thank you very much in advance!!!

---

### Post by Mark Phelps on 2014-03-03
You have the infamous Intel/AMD Switchable graphics -- which is not well supported in Linux:  [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355]("http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355")

---

### Post by Veronika_87 on 2014-03-04
Hi Mark, thank you for the link. I tried that, but that solution maybe works for Ubuntu 13.04 but unfortunately I have 12.04 now. I will try to reinstall ubuntu.

---

### Post by mastablasta on 2014-03-04
for newer card it is better to use latest version of ubuntu. or at least to update kernel in 12.04 using hardware enablement stack. i know this GPU is not really the latest one however newer ubuntu should have newer opensoruce drivers and will also install newer proprietary drivers. 

in many case AMD/Intel combo does work as it is supported by AMD (unlike nvidia which will not support it) but not always.

new 14.04 LTS comes out in April and is already in beta i believe.

---

