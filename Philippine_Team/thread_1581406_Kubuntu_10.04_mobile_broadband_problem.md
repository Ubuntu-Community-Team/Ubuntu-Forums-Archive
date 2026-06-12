---
title: "Kubuntu 10.04 mobile broadband problem"
date: 2010-09-24
forum: Philippine Team
---

### Post by omegadestroy on 2010-09-24
Hi

I'm completely new to the Linux world and badly needs help. I installed Kubuntu 10.04 two days ago and it has been a disaster because it has inconsistencies detecting the e1550 sun broadband. There are instances that it's working but after a reboot/hibernate it goes to a haywire. I need to delete and re-setup the mobile broadband connection settings once Kubuntu detects it after multiple reboots. Another thing I noticed is it's not being recognized as a USB modem to automatically connect as configured hence just a storage device when it's acting up. I'm also using Ubuntu 10.04 on the same netbook but I never got a problem using the same broadband connection. Is there a similar operation like:

gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules

On the GEdit window that opens, Type and Save:
SUBSYSTEM=="usb",
SYSFS{idProduct}=="1446",
SYSFS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

..to ensure that's Kubuntu's going to recognize e1550 and connect to the internet flawlessly?
Any help will be greatly appreciated. Thanks!

---

### Post by omegadestroy on 2010-09-24
Sorry if I started a new thread because I didn't find any thread or anything similar to this:guitar:

---

### Post by jtweaker on 2010-09-29
hi! do this

start **Adept** from the menu system select K Menu->System->Adept (Package Manager).[CENTER]
[/CENTER]
[LEFT]or[/LEFT]
[CENTER]
[/CENTER]
start **Adept** from the command line:kdesu adept




then from there type usb-modeswitch/usbmodeswitch (can't remember the right one) and see if its in you repositories. If it's there just install it if it's not download it from _[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)_ and follow the intructions given there



hope this helps! :)

---

### Post by jepong on 2010-10-04
hello omegadestroy

we have the same huawei modem and usb-modeswitch should do the trick...

> sudo aptitude install usb-modeswitch

... to make sure its detected, doing "lsusb" on terminal helps. Also, updating the the new KDE helps too.

---

### Post by omegadestroy on 2010-10-31
Thanks all! It's working now!

---

