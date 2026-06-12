---
title: "Network problems"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Ikuhhh on 2011-12-08
Hello everyone!
 
I have just installed Ubuntu 10.10 as a dualboot on my Asus K73S. The other OS is Microsoft Windows 7 (which I'm working on right now)
 
After starting ubuntu I tried to connect to a wireless network, but I can't even select "eneble wireless" even though in the help they say it should be there. 
So I decided to make a wirred conection. And I had the same problem... 
 
But when I boot on Windows 7 I can make connection with my network. Wireless and Wired.
 
Does anyone have an idea what the problem is? 
Ikuhhh

---

### Post by Jive Turkey on 2011-12-08
It may be that your wireless device isn't properly detected by ubuntu (yet).  If you could (while in ubuntu), open a terminal and run the following commands and post the output here we can probably get you going.

"lspci" (this will list all of the devices on the PCI bus)
"lshw -class network" (lists the network devices and some info about them)
"lsmod" (lists the modules currently loaded, which may or may not include the appropriate driver(s) for your wifi card)

I suggest you save the stuff to a text file in your windows partition or a thumb drive so you can access it after booting back into windows to post it.

---

