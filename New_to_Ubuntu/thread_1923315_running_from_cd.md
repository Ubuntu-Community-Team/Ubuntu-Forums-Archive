---
title: "running from cd"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by aj4rk on 2012-02-10
I have set up a cd to be able to run ubuntu 10.04 without installing it on my laptop. My laptop is an Acer and this version of Ubuntu does not recognize the driver for my wireless adapter (Broadcom 802.11g). I try to upgrade to the b43 driver but keep getting an installation error. What I want to know is this do to the fact I am running off the cd and not off the laptops hard drive.

---

### Post by Bucky Ball on 2012-02-10
Welcome.

You can't do that from the CD. There is nowhere to install the driver to as you are working from the CD and you can't save or install anything to that. (Think about it). The Broadcom card would work no problem with a hard drive install.

PS: All Ubuntu install CDs (or LiveCD) have the option to 'Try Ubuntu'. If everything else works I suggest you do a full install. You will be offered the drivers and firmware for the wireless when you update the first time or you will find them in 'Additional Drivers'. You shouldn't need to manually install, depending on the card model (most Broadcom cards are now a cinch). ;)

---

### Post by forrestcupp on 2012-02-10
I think it is possible to create a bootable USB stick and set it up to use a little bit of the memory for saving settings. Maybe you could try that out. Ubuntu.com gives you the resources you need to do that on the download page.

---

### Post by PapaGary on 2012-02-10
> **forrestcupp said:**
> I think it is possible to create a bootable USB stick and set it up to use a little bit of the memory for saving settings..
Yep. Go to [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and you can create a usb thumbdrive with "persistence", that is "space used to preserve files across reboots (Ubuntu only)"

---

### Post by C.S.Cameron on 2012-02-10
You can also extract usb-creator.exe from the Ubuntu iso using 7zip.
I find this works better than UNetbootin for making a persistent Ubuntu USB install.

---

