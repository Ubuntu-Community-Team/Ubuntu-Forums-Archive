---
title: "I need some help please !"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by new on 2008-10-10
Hello, I just did a dual boot with vista and ubuntu. I have a Dell Inspiron 1420 with bluetooth and integrated webcam.I have 4gb of Ram and 160 GB hard drive - 14.56 GB of which i dedicated to Ubuntu. Well i am having trouble getting my wireless to be activated ? but it recognizes the wireless card. Can someone please help me sort this out...at the moment this is the only problem i am having ! can someone please help me ?

---

### Post by tang0delta on 2008-10-10
Have you got any more information about the problem. What kind of wireless card are you using and how do you know that it is being recognized by Ubuntu?

---

### Post by new on 2008-10-10
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:7d:5c:27
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
       serial: 00:1e:c9:07:f0:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.105 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

thats the info...but my wireless light isn't ON ....on the laptop! i don't know y !

---

### Post by DGortze380 on 2008-10-10
> **new said:**
> *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:7d:5c:27
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
       serial: 00:1e:c9:07:f0:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.105 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

thats the info...but my wireless light isn't ON ....on the laptop! i don't know y !

The light means nothing. Are you using any kind of wireless security? WEP, WPA1, WPA2?

---

### Post by tang0delta on 2008-10-10
That's interesting. I have the same wireless card in my dell inspiron 6400 and my wireless light has never come on also. My wireless works fine though. Tell me, does your top gnome panel (where applications/places/system etc is) have a network indicator/ battery indicator etc? 

If not, try right clicking the panel >> add to panel >> notification area. then let me know if a little wireless indicator shows up.

---

### Post by new on 2008-10-10
It does have the 2 computers...showing the wired connection i am using now...and when i unlocked and tried to use the wireless....which does have a WPA security and i put in the passphrase and everything..nothing seems to be doing but the thing is ...i can't see the signal strength so i don't understand if it is trying to connect or not.

---

### Post by tang0delta on 2008-10-10
Well at least it recognises the card and lets you attempt to connect. When your putting in your encryption key are you first selecting the network from the list of available networks or are you putting all the settings in manually?

---

### Post by new on 2008-10-10
manually...i am putting in everythig manually cause i am not seeing available networks and they should be my wireless available.

---

### Post by tang0delta on 2008-10-10
Try adding the notification area to your panel and logging out an in again. When you log in you should see a wireless indicator, battery indicator and maybe a few other things in the top right corner. click the wireless indicator and see if you network is shown. sorry if i'm sounding really repetitive here but i had the same problem thinking my wireless was broken when all was really wrong was that the menu item for selecting my network was missing from the panel :tongue:

---

### Post by new on 2008-10-10
Its ok...i will log out and come back...but the thing is i am not seeing the wireless connections...its bugging me...lollol...well i will try again and come back..thanks tho and is there anything else i can do if i can't find it...

---

### Post by new on 2008-10-10
Ok well...i installed some program called wifiradar...its picking up my wireless...but now i can't see the 2 computers in the notification area !! and my wireless in the wireless manager should be on roaming mode right ??

---

### Post by tang0delta on 2008-10-10
i'm not too sure to be honest but don't give up! :tongue: you'll get it eventually with the right help. I'll have a look around too.

---

### Post by new on 2008-10-10
well...wifi radar ...got me connected to the wireless using my passcode...but i was wondering why the default manager couldn't or now isn't showing...sigh...

---

### Post by tang0delta on 2008-10-10
ah right congrats. I'm not familiar with that program but yeah roaming mode should be on.

---

### Post by new on 2008-10-10
Thanks alot for the effort, i really appreciate it...thanks alot. But do you know any way to get back ubuntu to see the wireless connections itself ?

---

