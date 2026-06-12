---
title: "Lubuntu 12.04 Wifi / Ethernet problem"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by renska on 2013-01-25
Hello.

I have tried to solve this problem on my own for 2 days now. Basically no thread in this forum has helped me. Both Ethernet and Wireless are down. When I first installed Lubuntu, ethernet was working but after trying to set up wifi, ethernet stopped working also. After this both connections were at state: UNCLAIMED.

I installed and removed packages (don't remember any more which packages, there were many) with help of this forum and the status remained the same.

Results of lspci -nn | grep 0280 -command:

08:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Results of sudo lshw -C network -command:

*-network UNCLAIMED
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: latency=0
resources: memory:e8000000-e8003fff
*-network UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=64
resources: memory:e8108000-e8109fff

Notice. I have no internet connection on my Lubuntu laptop, so I cannot just use sudo apt-get install ... -command. I have to manualla download the debian packages required to solve the problem.

So I'm hoping someone here could help me out?

Best regards,
Renska

EDIT: I managed to get the ethernet working. There was no b44 in the /etc/modules -file. After adding b44 and rebooting enabled ethernet connection instantly. Brilliant!

---

### Post by renska on 2013-01-25
I progressed on getting the Wifi working. I found a set of commands on one Finnish ubuntu forum. 

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

sudo apt-get purge broadcom-sta-common broadcom-sta-source bcmwl-kernel-source

sudo apt-get purge b43-fwcutter firmware-b43-installer

(Reboot)
sudo apt-get install b43-fwcutter firmware-b43-installer
(Reboot)
sudo gedit /etc/modules (add b43)

Now none of the networks are "DISABLED" or "UNCLAIMED"
Still, sudo ifconfig wlan0 up gives: "Error while getting the interface flags: No such device"
Indeed there is no wlan0, but there is no logical name in WLAN.

---

### Post by GordThompson on 2013-01-25
What does the following command produce?

```
rfkill list
```

---

### Post by renska on 2013-01-26
sudo rfkill list gives:

1: hp-wifi: Wireless LAN
            Soft blocked: no
            Hard blocked: no

---

### Post by GordThompson on 2013-01-26
> **renska said:**
> sudo rfkill list gives:

1: hp-wifi: Wireless LAN
            Soft blocked: no
            Hard blocked: no
Okay, that's good. From what I can see the b43 driver is the one that should work for you. Have you tried using the `modprobe` commands listed [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers") to unload all potentially conflicting drivers and then load *just *the b43 driver?

---

### Post by renska on 2013-01-26
Oh that's awesome! There was the problem. After setting 
sudo modprobe b43 WLAN showed wireless networks available. 
Thanks a lot! After all this work of installing and uninstalling drivers its crazy that the working of WLAN is up to something such a small thing.

---

### Post by GordThompson on 2013-01-26
You're welcome. Please remember to mark this thread as [SOLVED] using the "Thread Tools" link near the top of this page.

---

### Post by renska on 2013-01-29
Now this is going to make me insane.

I installed some updates to lubuntu because it requested. I had previously discarded updates that had anything to do with wlan. The updates didn't go well. Black screen appeared with lots of cryptic test and I could do nothing. After forced restart something has happened: install via terminal could not be done and Synaptic package manager or update manager wont work. When i tried to install something via terminal, it said that i should run sudo dpkg --configure -a (or something similar). I did and it said installation complete. Terminal was frozen. After opening the terminal again and trying to install program it requested to run the aforementioned command again.
I decided to reinstall lubuntu since I now understood how to set up wlan again.
After reinstall, I ran updates which I did also in the first install. Everything fine.
I started setting up wlan and after searching for the additional drivers, it downloaded and started to install broadcom drivers. BAM! Same black screen and same goddamn problem with package manager and update manager. Now installing lubuntu for 3rd time. Lets see what happens.

I'm starting to think if there is a hardware problem...

---

