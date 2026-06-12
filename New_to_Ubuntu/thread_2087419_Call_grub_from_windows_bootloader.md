---
title: "Call grub from windows bootloader"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by Rajatheprogrammer on 2012-11-23
I have multiple OS in my computer. When my computer boots i want to choose the OS from windows bootloader. When i choose a linux OS in windows bootloader, i want that linux OS's respective grub to be displayed. Ubuntu's grub to be displayed when i select Ubuntu and fedora's grub to be displayed when i select fedora in windows bootloader. How do i do this?. In detail please as im a newbe to linux.

---

### Post by philinux on 2012-11-23
An easy way is to use the easybcd app for windows.

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

It's free for home use. There's documentation on the site.

---

### Post by Rajatheprogrammer on 2012-11-24
> **philinux said:**
> An easy way is to use the easybcd app for windows.

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)
 

I tried adding entry for ubuntu and fedora using easyBCD by selecting  grub2 and its respective partition. Here it is

Entry #3
Name: ubuntu
BCD ID: {d62cdf7d-353a-11e2-9f99-88532e0aa38d}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub0.mbr

Entry #4
Name: fedora
BCD ID: {d62cdf7e-353a-11e2-9f99-88532e0aa38d}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub1.mbr

when i boot i get a terminal screen with "GNU GRUB version 2.00~beta4" title and
"grub>"

when i select grub legacy  type while adding entry and boot only a blank screen with a cursor blinking is displayed.
What do i do?

---

### Post by Mark Phelps on 2012-11-24
Most folks here use GRUB, not EasyBCD -- and will not hesitate to tell you to install GRUB -- which will NOT fix the problems you're having.

Your best bet is to go to the site Philinux gave you and check out their forums -- and post your own thread there if you can't find an answer.

---

