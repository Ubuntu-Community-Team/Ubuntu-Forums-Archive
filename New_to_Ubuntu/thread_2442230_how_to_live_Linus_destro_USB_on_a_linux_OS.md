---
title: "how to live Linus destro USB on a linux OS"
date: 2020-05-01
forum: New to Ubuntu
---

### Post by majukic on 2020-05-01
Hi Guys
first time Linux with Xubuntu OS and it's awesome.  Would like to create a live Linux USB that I can run on the Xubuntu OS computer. 
What USB boot software do you use? 
Is there something I have to do for Linux because I notice most USB boot software seems to favour Linux live usb in windows or Mac?
What do you use?
Also if you can answer I notice that Linux has things like /dd and other code just to load software.  Is there a very basic tutorial out there that explains how to load software in Linux?  Please link.

---

### Post by guiverc on 2020-05-01
Welcome to Ubuntu Forums.

I'll provide the following links for writing an ISO file to thumb-drive from multiple OSes

[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-ubuntu/14011](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-ubuntu/14011)
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020)
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-macos/14016](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-macos/14016)

(these links apply to all flavors, so Xubuntu too, you didn't provide a release so I didn't check if Startup Disk Creator is already installed on your release of Xubuntu or it'll need to be added. There are other tools though)

There are multiple types of ISO files, and the method of writing data to drive can vary on type, so not all ISO writing software will successfully write every type of ISO to a thumb-drive. The links I provided should work for Debian or Ubuntu ISOs (it was tested on Ubuntu ISOs)

I use `mkusb` myself to write my ISOs (nearly always, >95% of time now). See [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) but I'm always writing my ISOs from a Ubuntu box. 

My second most common tool is the `dd` command itself, but it's rather easy using that command to mistakenly overwrite something important (I overwrote a 2TB backup hdd, then a few months later a 12TB drive array... the second time had my finally stop using `dd` by default). I now only use `dd` on boxes that are stand-alone or not connected to network.

---

### Post by majukic on 2020-05-09
very helpful links cheers

---

### Post by mastablasta on 2020-05-11
i would juts boot them live session in virtualbox. if it's interesting i will install it.

---

