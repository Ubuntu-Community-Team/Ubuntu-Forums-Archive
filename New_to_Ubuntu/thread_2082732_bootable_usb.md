---
title: "bootable usb"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by geogur on 2012-11-10
i downloaded a iso image of ububntu put it on usb but need to make the usb bootable , not shure how to do this im going to replace  my drive in my ubuntu laptop and would like to do a fresh install. how can i make my usb ubuntu bootable

---

### Post by LiamOS on 2012-11-10
If you have simply coppied the .iso onto the usb, nothign will happen. I'd recommend using unetbootin to make the USB bootable.

However, if you've already done that, you can use gparted or fdisk to set the bootable flag on the partition.

---

### Post by 2F4U on 2012-11-10
Assuming that you are using Windows, here is another way how to create a bootable usb stick:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

### Post by geogur on 2012-11-10
> **geogur said:**
> i downloaded a iso image of ububntu put it on usb but need to make the usb bootable , not shure how to do this im going to replace  my drive in my ubuntu laptop and would like to do a fresh install. how can i make my usb ubuntu bootable

i think i found it im going to try it now on another pc to see if its bootable , i hope this works i want to replace the faulty drive

---

### Post by Cheesemill on 2012-11-10
Instructions for creating a bootable USB from your download can be found on the Ubuntu website:

[http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)

---

### Post by El Tito on 2012-11-10
I used LiLi to make my live usb   [www.linuxliveusb.com/](www.linuxliveusb.com/)   

You can make a bootable usb from a preexisting iso or you can select one in the program menu, and it will download it automatically and install it in the usb.

---

### Post by Bartender on 2012-11-10
Some USB thumbdrives just won't work.  I don't know why.  I've got half a dozen of them laying around here, and at least two of them refuse to get the job done.  Success on a couple of them so I don't think it's operator error.

---

### Post by greatsirkain on 2012-11-10
copy+paste=voilà:

"in windows (if you have a usb stick)  make it bootable with Sardu  selecting ultimate boot cd etc  (you can also add Ubuntu, SUSE and  windows, among others, so you have live OS's on there too) then when you  boot from your usb stick use grub or supergrub2 (from the utilities  menu I think) to detect all operating systems then just select the one  you want to use. A bootable usb stick with as many tools as you can get  on there will always come in handy for fixing your computer."

I'm a fan of Sardu 'cause you can get all your tools, utilities, live operating systems etc on to one stick the only downsides I noticed was I didn't get the option for persistence with the live Ubuntu so I couldn't save my settings & that the option to install hirens boot CD is disabled so you have to get that ISO yourself

---

