---
title: "Virtualbox horror. How to install Xen or OpenVZ in Ubuntu 12.04?"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by kramer65 on 2012-05-19
Hello,

I've been using Virtualbox for some years now and always used to like it. For the past one or two years it has been only headaches for me though. My last installation of Ubuntu 10.04 started doing total freezes more and more which always seemed to appear when I had Virtualbox running. I recently did a totally clean reinstall of Ubuntu 12.04 with which I never had any problems.

Two days ago I installed Virtualbox and it simply doesn't seem to get along well with Ubuntu. I installed a CentOS 6, a Ubuntu 12.04 desktop and a Ubuntu server 12.04 as virtual machines in Virtualbox. CentOS seems to work ok, but it runs extremely slow (booting takes about 15 minutes). Booting the virtual Ubuntu server makes my whole computer freeze, ending with me having to hit the reset button, and the virtual Ubuntu 12.04 desktop is worst of all: when trying to boot that machine my whole computer simply reboots without any message or warning. I retried booting all of these installs numerous times, but the all continue to have the same result.

So I don't want to touch Virtualbox anymore. the website OSalt.com [suggested]("http://www.osalt.com/virtualbox") Xen and OpenVZ. So I looked in the Software center but couldn't find any of the two. In Synaptic I found a package called openxenmanager which was described as a "*full-featured graphical management tool for xen using xenapi*". So I installed that, but when I hit the Super-button and search for things like 'xen', 'openxenmanager' or 'open xen manager' it can't find anything.

I don't really know how to install OpenVZ either.


Does anybody know how I can install either Xen, OpenVZ, or any other simple virtualisation package to replace Virtualbox?

All tips are welcome!

---

### Post by Cheesemill on 2012-05-19
You could try VMware Player:
[http://www.vmware.com/products/player/overview.html](http://www.vmware.com/products/player/overview.html)

---

### Post by kramer65 on 2012-05-19
Although I prefer Open Source software where possible I went to the website of VMware and downloaded the software. When reading the installation notes I read the following lines:
*[INDENT]If you have an Intel CPU that has VT-x support, you must verify that VT-x support is enabled in the host system BIOS. The BIOS settings that must be enabled for VT-x support vary depending on the system vendor.[/INDENT]*
Seeing that I was indeed installing 64 versions of the OSes and my CPU is rather old (6 years by now) I wonder if it could be that my CPU simply doesn't support that VT-x that well (I never heard of it btw). So I am doing one more test with Virtualbox by installing Ubuntu Server 32 bit. If that works I think I have enough to mess around a bit (I simply want to learn more about server management by playing around with it in a virtual machine).

Does anybody know if it makes sense what I am saying? Could it be that the possible lack of support for VT-x could be the problem which I am facing with Virtualbox? Because if that's true I suppose I wouldn't solve the problem by simply installing another virtualisation package.

---

### Post by ljw1 on 2012-05-26
You need to check if the virtualisation extensions are enabled for your cpu and motherboard. If these are disabled then the virtualisation software has to emulate everything. Virtualbox does this without warning you and the outcome is that the vm performance is woeful.

---

