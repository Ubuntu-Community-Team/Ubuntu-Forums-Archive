---
title: "Having Trouble With Wireless - New User!"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by xaxtree on 2008-05-17
Hello, I just installed Ubuntu as a dual boot today, and I have no idea on how to setup my wireless network.  At the moment I am wired, but I am usually wireless and I don't like being wired.  Is there anyone who could help me setup my wireless router to work with Ubuntu?

---

### Post by shadow-of-sin on 2008-05-17
What is the model of wireless card you have?

---

### Post by xaxtree on 2008-05-17
Well since its not external and its built into my laptop I have to look it up, is there anyway I can find out through Ubuntu, or just reboot and look in windows, and do you also need my router type?  Its a WRT54GX2 Ver. 2, and its linksys.

---

### Post by shadow-of-sin on 2008-05-17
What's the model of your laptop?

---

### Post by xaxtree on 2008-05-17
Acer Aspire 5100

---

### Post by dimopolous on 2008-05-17
I have a Dell laptop and I had to activate an external driver to go wireless, and I needed to use the wire connect to get the driver.  I also activated the connections for wireless and wire in properties.  Hope it helps!!:)

---

### Post by xaxtree on 2008-05-17
Well I don't even know if the makers of my wireless card in my laptop (which is internal) has drivers for linux, hopefully they do.

---

### Post by shadow-of-sin on 2008-05-17
There is a guide for your wireless:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Unfortunately the process is quite long winded as there is no native linux drivers so the windows drivers must be used with ndiswrapper.

---

### Post by xaxtree on 2008-05-17
Aw, ok thank you anyways.

---

### Post by xaxtree on 2008-05-17
Wait, that topic is a bit confusing, don't understand what BCM43xx is.  I mean I will probably figure it out.

EDIT: Also I just found out my network controllers, atleast the ones ubuntu detects
network controller(s):

Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Eman1955 on 2008-05-17
I just spent "xxxx" hours on this and my friend Ayuthia got me through it.

[http://www.linuxwireless.org/en/user...43andb43legacy](http://www.linuxwireless.org/en/user...43andb43legacy)

The instructions look fine. The only thing that I will mention is that if you don't have build-essential installed, you will not be able to compile the b43-fwcutter.



b43-fwcutter should be in the installation CD. To add it from the Terminal:

Code:  sudo apt-cdrom add



It will ask you for the CD. Insert it and it will be added. Then:

Code:   sudo apt-get update



will load the package lists into the system.

Code:  sudo apt-get install b43-fwcutter



It will install the package and then will ask you if you want to have it find the firmware for you. If you DO have an internet connection, say yes and it will install it for you.



If you do NOT have a working internet connection, make sure that you say no or cancel. You will need to download the firmware and place it in your home directory. Here are the files that you need:

[http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o)

[http://downloads.openwrt.org/sources...0.53.0.tar.bz2](http://downloads.openwrt.org/sources...0.53.0.tar.bz2)



Once they are in your home directory, go to the Terminal and do the following:

Code:



cd

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

tar xfvj broadcom-wl-4.80.53.0.tar.bz2

sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy



That should do it. This is the way that Ubuntu does it. The information above is based on their install script that comes with b43-fwcutter.

---

### Post by Raccoon1400 on 2008-05-17
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)
use ndiswrapper. Instructions here.

---

### Post by xaxtree on 2008-05-17
Oh thank you so much! I will do this right now, is there a way i can contact you if i need help, like through MSN or AIM?

---

### Post by KOTAPAKA on 2008-05-17
Man I hate this. You know if had looked up on the internet and in the forum you might have done it faster and you would have learned much more. Anyway I will give some help. Fwcutter will probably not work with your wireless card. I would give Ndiswrapper a try.

---

### Post by xaxtree on 2008-05-17
Oh don't worry I got it, it works now, eman's instructions helped a lot

---

