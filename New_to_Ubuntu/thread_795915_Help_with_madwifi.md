---
title: "Help with madwifi"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Lukky on 2008-05-15
Hello,
   I am trying to install madwifi. I guess that is the best app to get my Atheros wifi to work. 
   I am trying to follow the steps on the Madwife website which tells me to put my "eth0 down" I have tried that and I get no such device found. When I try to install madwifi I get tha wlan is still running. 
    I am also having problems with my NVIDIA driver. I turn off the X server and try the install and I get cannot open file. The file is located on my desktop. I downloaded it directly from NVIDIA. 
   I know both problems are probable my weakness with a command promt. 

Thanks Dustin

---

### Post by axor1337 on 2008-05-15
i just got my atheros working with out mad wifi  what specific wifi card do you have and in what brand model machine

---

### Post by Lukky on 2008-05-15
It is a HP dv6815nr. I want to say that it is Atheros 5007. I am running ubuntu 8.04 fresh install no mods.

Thanks Dustin

---

### Post by LakeWind on 2008-07-01
Did you ever get the wifi working with this laptop?

---

### Post by rijen on 2008-09-13
I have a HP DV6815nr also and madwifi works fine

Just use this driver and follow the instructions:

[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Installed it (OpenSuse 11.0 and Kubuntu 8.04 both 32bits) and it works fine

---

### Post by Crafty Kisses on 2008-09-13
Try the following command in Terminal:
```
sudo lspci | grep Atheros
```

If there is any output similar to that below, you need to install madwifi.
```
00:0e.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

If there is no output, try looking through [http://madwifi.org](http://madwifi.org), from there go to** Wiki --> Compatibility**, to see if your network adapter is supported.

---

