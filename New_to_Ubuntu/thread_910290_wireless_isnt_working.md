---
title: "wireless isnt working"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by patchido on 2008-09-04
well wireless doesmt work in ubuntu bit ir roes ion vista, ir doesnt evento recognize any signal wont fine ir

---

### Post by patchido on 2008-09-04
com on..... plz  :( i need internet :)

---

### Post by wolfen69 on 2008-09-04
what kind of wireless card is it?

---

### Post by porchrat on 2008-09-04
please copy and paste the ouput of this command:

```
lshw -C network
```

will let us know what card you are running

---

### Post by hotrod6657 on 2008-09-04
> **patchido said:**
> well wireless doesmt work in ubuntu bit ir roes ion vista, ir doesnt evento recognize any signal wont fine ir

It might help to post more information, like what version you're using, what kind of card it is, laptop/desktop, etc.  People can only help you with what you tell them.

And not to sound picky but it might not hurt to check your spelling a little.  It's just hard to read when every other word is poorly spelled.

Again, not trying to be mean about it, just a tip for down the road.  Might help you obtain better help from the forum

hotrod

---

### Post by patchido on 2008-09-04
> **hotrod6657 said:**
> It might help to post more information, like what version you're using, what kind of card it is, laptop/desktop, etc.  People can only help you with what you tell them.

And not to sound picky but it might not hurt to check your spelling a little.  It's just hard to read when every other word is poorly spelled.

Again, not trying to be mean about it, just a tip for down the road.  Might help you obtain better help from the forum

hotrod


srry about that... i did that post on an iphone because my wireless wasn't working :P


ill post my output when i get to my hoouse and connect via ethernet cable

---

### Post by patchido on 2008-09-04
```
pato@pato-laptop:~$ sudo lshw -C network
[sudo] password for pato: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:9b:4b:19
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:09:8b:67
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair
pato@pato-laptop:~$ 


```




i use hardy in a dell laptop - inspiron 1420
the rarae thing is that i have been more than 2 months using this and wirelesss never had failed

---

### Post by porchrat on 2008-09-04
> *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection

Your wireless module is disabled...we may need to see a dmesg ouput to see what has done it.

Please copy and paste this ouput (I know it is long, you may need to change the line limits in your terminal window to fit it all in - do this by going to edit in the top left corner I can't remember which tab this setting is under):

```
dmesg
```

Actually here is a thought...do you have a wireless switch on your computer?  and if so is it on?

---

### Post by Bölvaður on 2008-09-04
PRO/Wireless.. that might be the problem. I also had problems (not sure if it was driver or config I messed up) and couldn't connect even though I could see all the networks.

There have been many people past 2 weeks posting about problems with PRO/Wireless so you should see a lot of threads on these forums if you search for wlan0 and other related words.

What I did? Well I was lazy and installed xubuntu 7.10 and it is working like a charm, I don't have time for actual fixing :(

---

### Post by patchido on 2008-09-04
actually now im sucessfully running wireless.. not sure how but i enabled it for GUI the strange thing is that before that the option didn't appear :S thx anyway :D

---

### Post by Peter09 on 2008-09-04
Seen this before, make sure that your hardware switch on the laptop is fully over.

---

