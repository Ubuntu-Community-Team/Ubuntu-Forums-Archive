---
title: "Networking Card Not recognized"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Arkane308 on 2008-09-12
I am having some problems getting Ubuntu to recognize my networking cards that are in my laptop.  I have a Alienwae Sentia 3140m with a 1394 Net Adapter and a Realtek RTL8169/8110 Family Gigabit Wireless card. Does any one have any Help for me.  I also think that my graphics card is not working because the videos that are included in the examples folder failed to display but the audio worked.  I have an integrated graphics card X3000 i think but i am not certain on that.  Any help would be appreciated

---

### Post by SunnyRabbiera on 2008-09-12
well the realtek card might be able to work, as will the graphics card with proper tweaking.
For the more experienced users can you post your full specs?
I think there are fixes for your machine, as that hardware does work from what I know with linux its all a matter of tweaking.

---

### Post by Arkane308 on 2008-09-12
The specs for my computer are:
Intel Core 2 Duo T5500 @ 1.666GHz
1.99 GB of Ram
40 GB hard drive with about 21GB used

Under my Divice manager the specs for my display adaper is
Mobel Intel 954GM Express Chipset Family
The Network adapter Header has these under it
1295 Net Adapter
Intel Pro/Wireless 3945ABG Network Connection
Realtek RTL8169/8110 Family Gigabit Ethernet NIC

If you need any other info I will be glad to provide it.

---

### Post by bobnutfield on 2008-09-12
> Intel Pro/Wireless 3945ABG Network Connection

Your wireless should definitely work with Ubuntu.  There are a number of posts on the forum about it, but I am not sure if the module comes with the stock install.  Many have had to install the backport modules to get it working if it does not out of the box.  Type in a terminal:

> sudo lsmod

look for a module called ipw3945.

There is also a post from one who solved the issue with your wireless:

[http://ubuntuforums.org/showthread.php?t=890593&highlight=Intel+Pro%2FWireless+3945ABG+Network+Connection]("http://ubuntuforums.org/showthread.php?t=890593&highlight=Intel+Pro%2FWireless+3945ABG+Network+Connection")

---

### Post by Arkane308 on 2008-09-12
Sorry about that I found everything that i needed here 
[http://skzo.wordpress.com/2008/08/27/ipw3945-driver-on-ubuntu-hardy-heron/](http://skzo.wordpress.com/2008/08/27/ipw3945-driver-on-ubuntu-hardy-heron/)

---

