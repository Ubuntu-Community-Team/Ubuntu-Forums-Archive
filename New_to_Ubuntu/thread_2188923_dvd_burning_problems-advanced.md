---
title: "dvd burning problems-advanced"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-11-19
i cant seem to burn an iso to a dvd

i get this error message with k3b

No CD/DVD/BD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features such as audio track extraction, audio transcoding or ISO9660 image creation.

same problem with brasero and xburn

is there a program i could install from the spm to correct.tks

---

### Post by rburkartjo on 2013-11-19
and just check all my live cd 's are booting up fine so i know it is not my cd drive.

---

### Post by fantab on 2013-11-19
> **rburkartjo said:**
> and just check all my live cd 's are booting up fine so i know it is not my cd drive.

There still could be a 'Writing' issue with your CD/DVD drive.
I too have the same problem with my drive, I can read anything supported from it, but 'Writing' is an issue. Mine does not write from any OS with any burning application. And since then I only use USB.

Try cleaning the 'Lens' with any good 'Lens cleaning' CD/DVD. You can also do it manually, but I won't recommend it.

---

### Post by rburkartjo on 2013-11-19
tks that is probably the problem. weird cause i also can make a bootable flashdrive using a usb stick. probably is my computer it is a dell Latitude D630 laptop

---

### Post by rburkartjo on 2013-11-19
fan let me ask you a question. how do you get your iso to install on the usb stick. i can get the live version on a stick but when i try to install on the usb i get the error message that i cant because there is no copy on a cd/dvd. tks

---

### Post by fantab on 2013-11-19
I use 'dd' command to burn the .iso to the USB or use Unetbootin or 'Starup Diskcreator'. If UEFI 'dd' does not work, or creates problems. 
In your case it sounds like a bad burn or USB booting is not enabled in your BIOS. Try enabling USB booting and/or make the USB device, that is plugged in, as your first boot device.
That error sounds like your Bios is trying to boot from CD/DVD.

---

### Post by rburkartjo on 2013-11-20
tks fan. will give it a try and mark thread as solved if i can get it to work.

---

### Post by jimmyh1972 on 2013-11-20
Try xfburn application, works great with me.

---

### Post by rburkartjo on 2013-11-21
jim wont work with my laptop. must be my computer because it work great with the one i gave my daughter.

---

