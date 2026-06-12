---
title: "Unable to boot from USB"
date: 2017-01-22
forum: New to Ubuntu
---

### Post by cheese.biscuit on 2017-01-22
I've installed Ubuntu twice before, but just received a computer that's giving me trouble with it.

Model: Shuttle XPC SG31G

I'm able to get to the boot menu. These are my options:

[IMG]http://i65.tinypic.com/dwc4fc.jpg[/IMG]

I'm using a USB stick with files from [https://www.pendrivelinux.com/](https://www.pendrivelinux.com/). I was able to install Linux on a different computer with this drive and the files on it after failing with this computer. Whatever I select, the next thing that shows up is "verifying pool data," which is successful. I have switched out the CMOS battery after reading an old one can cause this. No luck.

I tried all the USB options earlier today, will be trying the rest a little later. But I suspect none of thrm are going to work, so I decided to ask here,

Any ideas on what I should try next?

---

### Post by sudodus on 2017-01-22
Welcome to the Ubuntu Forums :-)

It might be possible to 'pretend' that the USB drive is a hard disk drive. Boot with the USB drive plugged in, and enter the 'Hard Disk' submenu. You might find the USB drive listed there. In that case, put it on top of the boot list, and try booting.

See this link for more details, [Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by leunam12 on 2017-01-23
try using PLOP Boot manager on a CD or floppy; it will give you the option to boot from your USB stick.

[https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)

---

### Post by gordintoronto on 2017-01-23
+1 for PLOP

---

### Post by cheese.biscuit on 2017-02-01
Thanks, PLOP worked! AWESOME!

I'll go ahead and mark this as solved.

---

