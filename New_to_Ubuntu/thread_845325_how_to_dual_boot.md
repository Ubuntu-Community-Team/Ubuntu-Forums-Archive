---
title: "how to dual boot?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by jbocean on 2008-06-30
**How to best 'dual boot' and go back to having XP**

Have old compaq presario 6000 w/ Windows XP.
Installed Ubuntu Studio.
Tried and tried to get wireless working w/ Linksys WUSB-300N.
I found a thread sowewhere which seemed to address the issue across OS platforms.
Giving up on ubuntu ...
Want to go back to XP.
How to best 'dual boot' and go back to having XP load up when I turn on the computer?

---

### Post by bumanie on 2008-06-30
If still using ubuntu with windows. > sudo apt-get install startupmanager and you can use a gui to have windows as the first boot option. Startup Manager is under System --> Administration. Not sure if that's exactly what you are after. If you want a decreased grub timeout, you can > sudo gedit /boot/grub/menu.lst and find the timeout line and edit it to less than the default 10 seconds.

---

### Post by kansasnoob on 2008-06-30
The simplest way to make windows boot first if you want to keep Ubuntu and try to straighten this out is to install 

> startupmanager

from synaptic.

If you're going to completely remove Ubuntu I'd follow this guide (you'll have to either restore the Windows mbr or keep GRUB):

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

But, I've been playing with Linux Mint which is an Ubuntu derivative and I find that it does seem to have better wireless support. I can't swear by it because I'm still just playing but it's something to think about. Also I believe that 8.10 (aka Intrepid Ibex) is very much focusing on increased wireless support, but that's a few months down the road.

---

