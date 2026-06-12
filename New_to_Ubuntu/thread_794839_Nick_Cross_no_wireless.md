---
title: "Nick Cross no wireless"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by mehehool on 2008-05-15
hi My name is Nick cross I have just installed ubuntu 8.04 i think and i am running gnome 
i have an acer laptop 
I installed this on my professors suggestion and  
I have already erased vista 
and i have  no idea how to use this program 
further more my wireless drivers installed but 
my network does not show the option 
I have an external card but i dont know how to install it 
its a belkin n card and i have a trendnet n router
if u need anymore info i will gladly give it too 


also hi how was your day

---

### Post by HunterThomson on 2008-05-15
> **mehehool said:**
> hi My name is Nick cross I have just installed ubuntu 7 i think and i am running gnome 
i have an acer laptop 
I installed this on my professors suggestion and  
I have already erased vista 
and i have  no idea how to use this program 
further more my wireless drivers installed but 
my network does not show the option 
I have an external card but i dont know how to install it 
its a belkin n card and i have a trendnet n router
if u need anymore info i will gladly give it too 


also hi how was your day

What is the exact model # of your external bliken n wireless adapter?

---

### Post by mehehool on 2008-05-15
belkin part # F5D8073

---

### Post by Xiong Chiamiov on 2008-05-15
You may want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=539533"), especially post number 3.  It's odd, though, I'm not sure if it has a ralink chipset or not, since that person had to use ndiswrapper, but another was trying to compile the ralink drivers.

And, hello, sorry I couldn't help you yesterday.  Perhaps we get can a solution with others' help, eh?

---

### Post by mehehool on 2008-05-16
thanks bro i am still working on the solutions u gave me but i have another 
question. I have a atheros wireless chip installed in my laptop and linux says it is installed the drivers are installed it is enabled but in my network manager there is no wireless option is there any solution u know of for that

also i dont have my belkin disk anymore and i cant find a .inf on the web

---

### Post by HunterThomson on 2008-05-16
> **mehehool said:**
> thanks bro i am still working on the solutions u gave me but i have another 
question. I have a atheros wireless chip installed in my laptop and linux says it is installed the drivers are installed it is enabled but in my network manager there is no wireless option is there any solution u know of for that

also i dont have my belkin disk anymore and i cant find a .inf on the web

for the blinken you have to use NDIS wrapper.

For the atherose wireless car in your notebook you can use the MadWiFi driver.:guitar:O

Search for the HOW TO install the madwifi drive I remember seeing before.

---

### Post by ugm6hr on 2008-05-16
Let's start from the beginning.

What model Acer laptop?

Are you online with Ubuntu?  Can you connect with wired ethernet?

Can you copy / paste the output from the following (case sensitive commands):
```
lspci
lshw -C network
```

---

### Post by mehehool on 2008-05-17
ok Acer extensa 5420 
yes i can jack in but no wireless as of yet 
yes i have use those commands already

---

### Post by ugm6hr on 2008-05-17
> **mehehool said:**
> yes i have use those commands already

We need to see the output from the commands - we're not psychic!

---

### Post by mehehool on 2008-05-17
*-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1d:72:14:51:c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.10.101 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by ugm6hr on 2008-05-17
More questions, I'm afraid...

32-bit (i386) or 64-bit (AMD64) Ubuntu?

Definitely Ubuntu 8.04LTS / Hardy?

Can you check what Windows identifies the wifi as (somewhere in Control Panel / System, I think.

I think these are relevant: 
[http://www.uluga.ubuntuforums.org/showthread.php?t=792158](http://www.uluga.ubuntuforums.org/showthread.php?t=792158)
[http://www.uluga.ubuntuforums.org/showthread.php?t=766169](http://www.uluga.ubuntuforums.org/showthread.php?t=766169)
[http://www.uluga.ubuntuforums.org/showthread.php?t=789824](http://www.uluga.ubuntuforums.org/showthread.php?t=789824)
[http://www.uluga.ubuntuforums.org/showthread.php?t=734691](http://www.uluga.ubuntuforums.org/showthread.php?t=734691)
[http://www.uluga.ubuntuforums.org/showthread.php?t=715187](http://www.uluga.ubuntuforums.org/showthread.php?t=715187)

---

