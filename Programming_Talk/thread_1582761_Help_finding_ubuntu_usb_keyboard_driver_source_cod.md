---
title: "Help finding ubuntu usb keyboard driver source code"
date: 2010-09-26
forum: Programming Talk
---

### Post by cpsusie on 2010-09-26
For a project at school I am supposed to find and analyze a linux usb keyboard driver.  I am having the damndest time finding the source code for whatever one came with my ubuntu (Lucid, x64, usb driver).  Can someone please tell me how to find this source code (and what the driver that Lucid uses by default is called, where the compiled version is, how to get the source code, etc?)  I am completely new to this kind of programming so please remember that when you give hyper technical answers.  I just want to know how to get the code so I can look at it and have a basis to start asking questions.  Please help.  
Thanks!

---

### Post by spjackson on 2010-09-27
Here are a few hints.

Get kernel source.
```

$ sudo apt-get source linux-image-$(uname -r)

```Find and view source (assuming linux-2.6.32).
```

$ cd linux-2.6.32
$ find . -name "*k*b*d*"
$ view drivers/hid/usbhid/usbkbd.c

```Or view/download single source [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/usbhid/](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/usbhid/)

---

