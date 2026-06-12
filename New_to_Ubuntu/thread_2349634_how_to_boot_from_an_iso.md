---
title: "how to boot from an iso?"
date: 2017-01-16
forum: New to Ubuntu
---

### Post by spankstergangster on 2017-01-16
so i just built a computer 3 weeks ago and i put ubuntu 16.10 on it. im ready to boot windows up but how do i do it without a disc or USB. the only USB i have was the one i used to boot ubuntu and i cant figure out how to wipe it. i want windows because wine does not work with windows steam games. so how do i boot

---

### Post by Frogs Hair on 2017-01-16
You can format the usb from Ubuntu which can then be used to create a bootable Windows USB. When the USB appears in the left pane of the file manager right click to see the format options.There are instructions available for creating a bootable Windows device  from Linux from various sources on the web.

---

### Post by Impavidus on 2017-01-18
On the other hand, then you will no longer have your live usb, which can be a great tool to fix a broken Ubuntu system. Consider buying an extra usb drive. You should be able to get one for about €8.

---

### Post by sudodus on 2017-01-18
I agree with *Impavidus*, keep the Ubuntu boot drive and get another USB drive for Windows.

You can use ***mkusb-nox*** or ***mkusb-dus*** alias guidus to make a USB boot drive (working in Ubuntu). See the following links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/gui#Installation](https://help.ubuntu.com/community/mkusb/gui#Installation) with details to get the not yet released mkusb-dus alias guidus from the unstable PPA.

[Making a USB drive to install Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

---

### Post by mastablasta on 2017-01-19
> **spankstergangster said:**
>  i want windows because wine does not work with windows steam games. 

also, that's not true. it does work but you need to install steam inside wine and ofcourse not all games work well (=rating gold or higher).

---

### Post by C.S.Cameron on 2017-01-20
Some of the Ubuntu installers such as Startup Disk Creator make a ISO9660 partition that can be a pain to get rid of.
The Wipe function of mkusb is an easy way to get rid of this partition and reset the drive to as new condition:

[https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

mkusb can also be used to install Windows:

[https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

However my understanding is that Steam is native to Ubuntu:

[https://linuxconfig.org/how-to-install-steam-on-ubuntu-16-04-xenial-xerus](https://linuxconfig.org/how-to-install-steam-on-ubuntu-16-04-xenial-xerus)

---

