---
title: "Hangs on Purple Load screen chmod issue?"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by Fruitsnacks on 2013-01-30
I'm having an issue: Had windows 7 installed on my Toshiba Satellite P200 - RT2. I had a USB drive with Ubuntu 11.10 so I installed using the USB. I was using the 2GB USB drive to boot from.  I went to do the updates and it said there wasn't enough space to run the 511 updates. So, I took out the USB stick and put Ubuntu 12.04 on it and tried to install it.

**Issue: It's hanging up on the purple "Ubuntu" load screen with "loading dots"...hangs there for hours. When I press F12 it reveals a bunch of errors and at the very bottom the texts reads:

chmod: /root/usr/sbin/update-initramfs: no such file or directory

I've tried some trouble shooting myself by:
google searching and using this forum's search bar and the closest I could get so far are steps from this link:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

If I'm a total newb and you can post a link to a fix I'm sorry I started this thread but I really appreciate your time and help.
If there is any more information you need from me I'll provide it asap.
Fruitsnacks

---

### Post by NikTh on 2013-01-30
Hi ,
do you want to install Ubuntu 12.04 IN to the USB or IN to the Hard Disk Drive ? 

If the second , then 

You must use a program like [Unetbootin](http://unetbootin.sourceforge.net/)
OR
you can follow this guide : 
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Then you will be able to boot from the USB (configure BIOS to boot first from USB) and install Ubuntu to the Hard Disk.

Thanks

---

### Post by Fruitsnacks on 2013-01-31
Thanks! 
If this changes anything...Windows won't boot. If I boot from the Hard Disk it goes straight to a black screen with a flashing cursor and sits there. It was working as well as Windows works before I did the USB install and now...nothing.
There is no OS currently installed to work with right now. I'll look through you're recommended help and go from there.
Fruitsnacks

---

### Post by Fruitsnacks on 2013-01-31
I cleaned 12.04 off of the USB drive and re-installed it for the 3rd time. At the end of the process it added a boot loader. I booted the Toshiba with it and it came to the same chmod issue. Then proceeded passed it. Code said something about bluetooth. 
Anyway it booted and launched 12.04.
Thanks for your help.

I decided to go ahead and install it to the HDD. I went through the install process and when rebooting(without the USB drive) it came to a black screen with a flashing cursor and hung up. Rebooted with teh USB drive and boots fine. It shows that the HDD has the Ubuntu files on it. I'm fine with booting from the USB(not lap friendly with stick hanging out the side of it) but if the files are on the HDD why am I not able to boot from them. 

Thanks for your help and time,
Fruitsnacks

---

### Post by NikTh on 2013-02-01
Probably the grub-bootloader installed to the USB and not to the HDD - MBR. 

Use this program : [boot-repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu) to fix the grub installation. 
You will need a live media of Ubuntu (CD/DVD/USB) and boot from there and follow the instructions. 
It would be useful to provide here the produced link.

Thanks

---

