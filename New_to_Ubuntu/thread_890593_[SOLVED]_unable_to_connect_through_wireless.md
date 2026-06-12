---
title: "[SOLVED] unable to connect through wireless"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by macvr on 2008-08-15
hi, i'm unable to connect through wireless, but able to connect through my ethernet...
it was working previously but now after i tried from this page
[http://ubuntuforums.org/showpost.php?p=5074972&postcount=11]("http://ubuntuforums.org/showpost.php?p=5074972&postcount=11")

my wireless is not working!!!

is there a system restore facility in ubuntu?

---

### Post by macvr on 2008-08-15
anyone knows what to do?

i even tried uninstalling the nework manager ,network manager gnome & reinstalling...
 still the wireless network doesnt work...

guess i messed up in the unlock procedure somewhere... !!!!!!!!!!

---

### Post by halitech on 2008-08-15
does your wireless still show as listed if you do an ifconfig in the terminal?

---

### Post by macvr on 2008-08-15
> **halitech said:**
> does your wireless still show as listed if you do an ifconfig in the terminal?
it shows 2> eth0 & lo

i think the second Lo is my wireless

---

### Post by Crafty Kisses on 2008-08-15
> **macvr said:**
> it shows 2> eth0 & lo

i think the second Lo is my wireless

Post the following output:
```
lshw -C network
```

---

### Post by macvr on 2008-08-15
> **Codename said:**
> Post the following output:
```
lshw -C network
```
this is what i get


WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:16:36:2b:c2:6c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5789-v3.49a ip=192.168.1.2 latency=0 module=tg3 multicast=yes

---

### Post by macvr on 2008-08-15
guys,!!! need any other info?

---

### Post by halitech on 2008-08-15
> **macvr said:**
> it shows 2> eth0 & lo

i think the second Lo is my wireless

Lo is for the local or loopback address and is not your wireless. 

I'm not all that familiar with intel cards but it looks to me like Ubuntu is seeing the card and has it recognized, I wonder if it needs to just have the connection set up manually

---

### Post by macvr on 2008-08-15
the wireless was working fine till i did what was in that post, i'v given above....
after a reboot it stopped working....
i wonder if its the problem with unlocking???

how do i set up my connection manually?
_or is there a system restore in ubuntu, _so i could go back to the config before the time i messed up my sonfig?

---

### Post by halitech on 2008-08-15
do you have the Network Manager icon up by the clock? If you do, left click it and select manual configuaration and see if you have the wireless option in there

---

### Post by macvr on 2008-08-15
> **halitech said:**
> do you have the Network Manager icon up by the clock? If you do, left click it and select manual configuaration and see if you have the wireless option in there

when i left  click - in manual config- i dont see any wireless options[have attached pics]
but when i right click i get edit wireless option

---

### Post by john test on 2008-08-15
Normally ifconfig should show eeth0 as ethernet, eth1 as wireless and lo as local loopback.
the lshw -C network shows both ethernet and wireless NICs
If you do ifdown eth1 that would shutdown wireless but it would show as down in ifconfig
That seem like no driver on the wireless card.

If it were me I would just reload linux but I just have a concept box with nothing on it to worry about

Do you know how to remove and reinstall hardware devices and drivers in linux?  HOpefully a more knowledgeable individual can tell us how to do the hardware driver install in linux:)

---

### Post by bobnutfield on 2008-08-15
In a terminal, type:

> sudo ifconfig -a

This will show all your network hardware, even if it is down.  Here is a link that may be of use to you:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Post back if the above command shows no wireless hardware.

---

### Post by macvr on 2008-08-15
sudo ifconfig -a  shows only eth0...



eth0      Link encap:Ethernet  HWaddr 00:16:36:2b:c2:6c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2b:c26c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1132259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:843424592 (804.3 MB)  TX bytes:314034362 (299.4 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:757372 (739.6 KB)  TX bytes:757372 (739.6 KB)


will checkout that guide and post back

---

### Post by macvr on 2008-08-16
i was always wondering what happened to the logical name of my wireless, it was not displayed in any of the commands i tried ![check above for my _lshw -C network_ list> no logical name for my wireless]

:KS@bobnutfield> thanks for that documentation!!!

i nearly went through all the commands trying to understand everything[though a lot of things went over my head!!!i'm in noway a computer literate]
when i get nearly towards the end there was a line about the laptop's _Hardware switch_, it was only then that the bulb glowed over my head!!!
tried the hardware switch[which i had not used in months! not even in XP] and rebooted, and everything works:):guitar:

also my wireless has been named!!!:lolflag:

but i dont understand how that switch was activated:confused: but i guess these things happen

```

now my ifconfig shows:

eth0      

lo        

wlan0     

wmaster0  
```:guitar:

_moral of story: check the simplest things first!!!_:) and to read the documentations first !

thanks to all who helped:KS

---

