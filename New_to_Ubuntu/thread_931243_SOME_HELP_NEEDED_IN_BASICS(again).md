---
title: "SOME HELP NEEDED IN BASICS(again)"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by sunlover on 2008-09-27
I have Ubuntu 7.10 dual booted with Windows XP on my laptop.
I access the Net thru Windows XP using an OPTION GX 0202 pci wireless card.
I am keen to get into Ubuntu but am frustrated by lack of direct internet access.
In searching this and other forums I am getting close to a solution but need some clues on some basics(again).

_CASE 1_“oztules” on pharscape 3G forum has achieved successful connection on SUSE 10.2 with above card. Part of his method was to edit **/etc/modprobe.conf.local** with details of card vendor and product(ie. add: **options usbserial vendor=0x0af0    product=0x6701**). When I open this file with gedit(as root) this file is empty.
His next step was to edit **/etc/sysconfig/kernel** changing:
[B]# 
MODULES_LOADED_ON_BOOT="" 
 to 
# 
MODULES_LOADED_ON_BOOT="usbserial"[/B] 
When I open this file with gedit(as root) this file is also empty.
He then goes on to configure wvdial(which I can follow).

_CASE 2_
“sharke” in these forums method to set up a different modem to mine   is:
_Quote_:To set up modem set usbserial to modem:
In terminal- [B]sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280[/B] 

You now have your modem activated- _Unquote_.
If I run this command will the amended vendor and product no's I get output:
[B]insmod: error inserting '/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko': -1 File exists 
bruce@bruce-laptop:~$ CC[/B]
He then goes on to configure ppp. 

It would seem both methods are inserting a module into kernel which is driver for appropriate card/modem.
I think the above module is the wrong one for my card and I guess I need a handle on inserting correct one.
I need a better understanding of what is trying to be achieved  here before proceeding further.
Any advise/suggestions gratefully accepted.

sunlover

---

### Post by bumanie on 2008-09-27
Apparently intrepid ibex is much, much better with wireless than hardy is - it's only one month to go until its release. Intrepid alpha 6 has some great reports re wireless connectivity - Canonical were aiming to have wireless improved for intrepid and by recent reports, they have succeeded.

---

### Post by hyper_ch on 2008-09-27
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by sunlover on 2008-09-28
Have reposted this thread to Networking & W/Less forum
sunlover

---

