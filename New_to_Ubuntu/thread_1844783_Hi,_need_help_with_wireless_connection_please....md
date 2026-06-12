---
title: "Hi, need help with wireless connection please..."
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Noniyobis on 2011-09-15
Ok, im new so please list any steps one by one. Heres my case. Im using ubuntu 2.8 ultimate. Wanna connect to my wireless router which is my smartphone. Works perfectly in win enviro. Dont know jack about linux commands except the basics eth0 and ifconfig. Now heres what happens, I start wifi radar, my wireless network shows up. Sometimes the preferences win comes up showing wlan0 which I cant seem to do much with. When I highlight my network and press connect it says aquiering ip address dhcp. But, wifi radar crashes as I see the red explosion icon. Sometimes it says I need to update rhe profile for connection really lost walk me rhrough? Thanks

---

### Post by MG&amp;TL on 2011-09-15
Sorry, I think I must be missing something..."ubuntu 2.8 ultimate" -there's never been a 2.8 release and there will never be an ultimate version...clarify?

---

### Post by bkratz on 2011-09-15
> **MG&TL said:**
> Sorry, I think I must be missing something..."ubuntu 2.8 ultimate" -there's never been a 2.8 release and there will never be an ultimate version...clarify?


Here is the link for 3.0!

[http://ultimateedition.info/](http://ultimateedition.info/)

---

### Post by Noniyobis on 2011-09-15
Hi you see im booting said operating system directly from a flash drive via usb. Does that help? thanks, it has a an option to install a 10.x ver which I havent done due to partion and possible memory as well. But, yes there is a boot up message saying ver.3.x.x  any help? its a network issue...

---

### Post by anewguy on 2011-09-15
With the system booted on the USB drive and being sure the adapter is plugged in (if it's external), please post back the output of the following:

- lsusb

- lspci

That should let us know what adapter you have.  There's no use in us asking you for more information until we see that.

Dave ;)

---

### Post by Noniyobis on 2011-09-15
Will do thanks. And now...

---

### Post by Noniyobis on 2011-09-15
Lsub says, 7 enrties all begin bus005,,4,3,2,1,1 device ld all seven 001,,1,1,1,3,2etc id linux foundation 1.1 root hub they all have what seems to be hexagonal binary last three say imc networks  sandisk corp., linuxfoundation 2.0root hub

---

### Post by Noniyobis on 2011-09-15
Lspci intel N10  family integrated graphics same more or less display controller audio. Last, network comtoller 02:00.0 network contoller atheros comm ar9285. Do need to be more specific let me know. Any specific info needed can be solicited, thanks

---

### Post by Noniyobis on 2011-09-15
The network wireless entry also says pci express in () then rev 01...

---

