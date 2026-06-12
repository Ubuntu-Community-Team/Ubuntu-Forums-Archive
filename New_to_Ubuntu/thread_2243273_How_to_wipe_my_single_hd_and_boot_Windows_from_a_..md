---
title: "How to wipe my single hd and boot Windows from a .iso from a usb"
date: 2014-09-07
forum: New to Ubuntu
---

### Post by goosebagelftw on 2014-09-07
I'm a complete noob at Ubuntu and Linux and I only installed it so I could get 8.1 and do some stuff on it. I personaly don't like it and it's too complicated for me. I've looked at countless tutorials and watched lots of videos but I'm still stuck and confused. I'm tired of typing stuff into a terminal and everything. Is there a less complicated way of doing this
? Also I want to format my single 1 TB hd and boot from my 8 gb usb.

---

### Post by coffeecat on 2014-09-08
Not a Tutorial

*Thread moved to **New to Ubuntu**.*

---

### Post by grahammechanical on 2014-09-08
Let me if I understand you correctly. You dont want Ubuntu. You do not like Ubuntu but you expect Ubuntu users to explain how to create a Windows 8 install USB memory stick and how to use it to install Windows 8. And you expect that help after complaining about the operating system that we use.

The only advice I can give to you is that you should be asking for help on a Microsoft forum.

---

### Post by Vladlenin5000 on 2014-09-08
> **grahammechanical said:**
> The only advice I can give to you is that you should be asking for help on a Microsoft forum.

+1

Not the first with similar requests and certainly not the last.

---

### Post by uRock on 2014-09-08
Use WinUSB, but you will have to run a few more commands in a terminal to get there.
```
sudo add-apt-repository ppa:colingille/freshlight
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/colingille-freshlight-trusty.list"
sudo apt-get update
sudo apt-get install winusb
```Directions taken from here [http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu)

I've used this program to create a bootable Windows 8.1 installer. This may not work with OEM installs.

Cheers & Beers,
uRock

---

### Post by Mark Phelps on 2014-09-08
You can boot the Windows installer from a USB stick/drive but you can not boot and run Windows from a USB stick/drive.

You should post on a Windows 8 forum for details -- suggest eightforums.com

---

