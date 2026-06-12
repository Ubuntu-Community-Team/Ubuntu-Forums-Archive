---
title: "82540EM Gigabit Ethernet Controller Problems"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by BundyBloke88 on 2008-11-18
Hi I downloaded Ubuntu a couple of days ago and put it on my laptop, i liked it so much that i installed it on my Dell GX270 as well but im having troubles getting the internet to work, everything works fine on the laptop Ethernet connection and Wireless but the dell ethernet isnt working, i downloaded the update which gave me the correct driver for it but it wont let me check the box in the network icon on the toolbar, i ran "sudo lshw -C Network" and it come up with:
 *-network DISABLED      
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s

im not running dual boot on this pc its only Ubuntu, could someone please tell me how to enable the ethernet device,

cheers

---

### Post by Peter09 on 2008-11-18
Whoops

---

### Post by Peter09 on 2008-11-18
As a first pass - check that any Hardware Switches on your Laptop for your wireless card are on.

---

### Post by BundyBloke88 on 2008-11-18
its not my wireless on my laptop thats the problem, the laptop works fine, its the Ethernet on my main PC that i need to enable.

---

### Post by Peter09 on 2008-11-18
And you have a good cable connection between your machine and a switch/router? What are the colours on the lights at on the card?

---

### Post by BundyBloke88 on 2008-11-18
Yeah the connection is good I tested it through the laptop with the same cable and didn't have a prolem. I was just wondering if there is an overide command that I could type in the terminal to enable it. I read another post and a guy said the same thing happened to him when he downloaded the patch and it took him hours to get the internet back up but he didn't e×plane how to do it in the thread.

---

### Post by Peter09 on 2008-11-18
couple of thoughts

can you post the contents of the file

/etc/network/interfaces

and what happens on the command

```
sudo /etc/init.d/networking start
```

---

### Post by BundyBloke88 on 2008-11-19
For /etc/network/interfaces i got:
auto lo
iface lo inet loopback

and for sudo /etc/init.d/networking start i got: 
* Configuring network interfaces...                                     [ OK ]

---

### Post by Peter09 on 2008-11-19
Check that you LAN card is enabled in your BIOS. (Is it an onboard card?)

---

### Post by BundyBloke88 on 2008-11-19
Yes its an onboard card and it was enabled in the BIOS menu.

---

### Post by BundyBloke88 on 2008-11-20
Ok found and fixed the problem. installed Ubuntu 8.10 and found out that the Ethernet card wasent putting out a mac address so all i had to do was get the cards mac address off the router and then add it into the /etc/network/interfaces file the instructions for that are here 
[http://www.howtogeek.com/howto/ubunt...ess-on-ubuntu/](http://www.howtogeek.com/howto/ubunt...ess-on-ubuntu/)

then when the network reset i was able to click on the auto ethernet check box and everything worked.

---

