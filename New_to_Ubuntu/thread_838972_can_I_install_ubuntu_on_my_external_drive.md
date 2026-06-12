---
title: "can I install ubuntu on my external drive"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by fazillatheef on 2008-06-24
I just wanted to know whether i can install linux on my external hard drive and use it like a live cd.. And can I keep the file system as fat32 itself..so that I can use the remaining space as storage when I plug it into a windows system.

---

### Post by gtdaqua on 2008-06-24
Of course, you can. But you should also know how to boot from a USB HDD.

---

### Post by mrsudo on 2008-06-24
you can easily install ubuntu on an External HD.  
the only problem im seing with this is many files in the installation are hardware specific.  

you would have to do an installation similiar to pendrivelinux.

---

### Post by golgo13 on 2008-06-24
you can run linux using qemu to emulate in windows off a pen drive:

[http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)

but I would not recommend this as you loose all the linux performance advantages

you can run ubuntu off a pen drive (if it has the capacity):

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

booting from usb is easy; go to the bios screen (press ctrl alt esc or f2 depending on your system)before windows launches, you may need to be quick!

then change the boot order i.e. move the usb option above the HDD
follow the instructions its pretty straight forwards

if you have a small pen drive then you may be better off with one of the smaller distros like puppy linux

[http://www.pendrivelinux.com/2006/03/25/puppy-linux-on-usb/](http://www.pendrivelinux.com/2006/03/25/puppy-linux-on-usb/)

have a look at pendrivelinux.com there are loads of usb boot options

---

### Post by golgo13 on 2008-06-24
btw mrsudo I like your flag :)
I was watching the cbc marc emery doc yesterday - very interesting!
sorry for going WAY off topic :)

---

