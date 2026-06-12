---
title: "Newb WiFi Problems Latitude D410"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by BBaumer on 2012-06-06
I just installed BackTrack 5 R2 on a Dell Latitude D410. I can connect to my home network via ethernet, but I'm having issues with WiFi. The F2 function key should turn WiFi on, but it's not working for me (the WiFi light doesn't light). When I right click on the Network Manager icon, Enable Networking is checked, Enabled Wireless does not show up at all.
 
I've very new to Linux. I searched a couple forums for assistance. It appears my system and network card are compatible. Below are some of the commands I found in other threads, so I figured I'd post them for further details.
 
```

root@bt:~# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux
 
root@bt:~# lspci | grep -i network
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2]
Network Connection (rev 05)
 
root@bt:~# iwconfig
lo no wireless extensions.
 
eth0 no wireless extensions.
 
root@bt:~# lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751
Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
     Kernel driver in use: tg3
     Kernel modules: tg3
 
--
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2]
Network Connection [8086:4220] (rev 05)
     Kernel modules: ipw2200

```

---

### Post by Gleichsnerd on 2012-06-06
When you access the internet via ethernet, open up the "Additional Drivers" application. There should be a Broadcom driver on there that should get you up and running.

Welcome to the Ubuntu Community! (and all that jazz)

---

### Post by BBaumer on 2012-06-07
Thanks for the assist. I do not have the "Additional Drivers" application though. I did some research and managed to install "Hardware Drivers" app. As far as I can tell, this is the same app, just renamed (newer version is Additional Drivers). When I launch this app, it does a quick search, then says "No proprietary drivers are in user on this system." and the window is blank. Where do I go from here?
 
Another individual suggested updating the firmware and pointed me here:
 
[http://mmc.geofisica.unam.mx/debian/...mware-nonfree/](http://mmc.geofisica.unam.mx/debian/...mware-nonfree/) 

Look for the file: firmware-ipw2x00_0.35_all.deb (18-Jan-2012 22:32 511K). Is the latest.
Just do: dpkg -i firmware-ipw2x00_0.35_all.deb
The driver is for both ipw2100 and 2200.

I tried this, but am unsure where to save the file to so that the command will run correctly. For now I have it in /lib/firmware/ipw.
 
```

[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][COLOR=black][COLOR=red]root@bt[/COLOR]:[COLOR=royalblue]~[/COLOR]# dpkg -i firmware-ipw2x00_0.35_all.deb
dpkg: error processing firmware-ipw2x00_0.35_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 firmware-ipw2x00_0.35_all.deb[/COLOR][/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman]
```[/FONT][/SIZE][/FONT]

---

