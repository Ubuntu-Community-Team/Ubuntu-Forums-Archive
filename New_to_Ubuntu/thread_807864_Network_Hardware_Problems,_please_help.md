---
title: "Network Hardware Problems, please help?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Crazy_Andt333 on 2008-05-26
Hi, first of all i would just like to say im a compleat Ubuntu 
n00b, but im tired of Windows Xp, so i decided to try out Ubuntu Studio. It looks great with loads of free stuff but i cant figure out how to connect online, i have a BT Voyager 1040 PCI Adapter and a BTHomeHub. i understaind that my driver CD for the NIC is not going to work, so i was wondering if anyone would be able to at least push me in the right direction of where to go next? Many THX!!

---

### Post by johnnyfox on 2008-05-26
OK, I am new to this, but when i had trouble getting a wireless connection. i first check that i had enable networking by clicking the icon network in administration and then hardware drivers to see if my driver was there. It wasn't so i connected using LAN (hard cable) and went to synaptic package manager searched for a driver sniffer which there are a few and the driver appeared (which was nice!) just had to tick the box next to it in hardware drivers and wireless connection came up in network. This may not be the same thing but might spark something off.

---

### Post by mapes12 on 2008-05-26
I also have a BTHomehub set up here.

Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

---

