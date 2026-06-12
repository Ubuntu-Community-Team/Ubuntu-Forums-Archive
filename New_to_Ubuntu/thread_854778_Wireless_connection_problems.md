---
title: "Wireless connection problems"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Bix in Austin on 2008-07-09
I have been unable to get on the internet since I reinstalled Hardy 8.04. My prior install was a dual boot with w2k and it found the nic and got on the internet without my doing anything. This time I have only Linux on this computer. I have a DLink wireless card and when I look it is recognized by the OS. It is shown in the hardware drivers with a third party driver. I think that I need to get to the driver setup to get the connection set up. That is what I had to do with windows and that os would not get it working. How do I go about getting this problem remedied?

---

### Post by jimrz on 2008-07-09
It would be a great help if you posted which D-link card and what chipset it is running . Then others using the same card could explain what they did to get theirs working.

---

### Post by Bix in Austin on 2008-07-14
Sorry for the delay in replying. My wireless card is a DLink DWL-AG530.I checked for it with lspci but it doesn't show up. I have tried ifconfig and iwconfig but it isn't in either of these either. I am pretty new at Lunux so I am currently scratching my head about what to do next.I am using my old laptop to make this connection currently but would very much like to get the Ubuntu PC back on the internet again.

---

### Post by weirdfox on 2008-07-14
I think your card use the madwifi driver and you will need to install the restricted modules package 

```
 gksudo apt-get install linux-restricted-modules 
```

For more info on the madwifi support for your card look here:
[http://madwifi.org/wiki/Compatibility/D-Link#DWL-AG530](http://madwifi.org/wiki/Compatibility/D-Link#DWL-AG530)

And this thread (it's pertty old, but may contain valuable infos)
[http://ubuntuforums.org/showthread.php?t=200375](http://ubuntuforums.org/showthread.php?t=200375)

Good luck !

---

### Post by Bix in Austin on 2008-07-14
I just found a note that tells me how to find the information for my wireless card. It is:
Product: AR5212/AR5213 Multiprotocol MAC baseband processor
Vendor: Atheros Communications Inc.
Physical id: c
Bus Info: pci@0000:00:0c.0
Logical Name: wifi0
version: 01
serial: 00:11:95:bf:c0:96
width: 32 bits
clock: 33 MHz
capabilities: bus_master cap_list logical ehternet physical wireless
configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath pci multicast=yes wireless=IEEE 802.11a
I sure hope this is enough info to be of some help. 
Thanks in advance for any and all suggestions.
Bix in Austin

---

### Post by Bix in Austin on 2008-07-15
My computer suddenly got very unstable so I rebooted it in the recovery mode and now I have an internet connection and the screen resolution is back to normal instead of the large size I had been having. I am good for now.

---

