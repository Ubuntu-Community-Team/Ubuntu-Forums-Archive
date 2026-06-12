---
title: "Wireless connect option is disabled/grayed out?"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by SoberWarlock on 2012-10-26
I just installed Xubuntu and I noticed that wireless detection isn't working. So does this release come with a pre-built in wireless driver? When I use wired connection that works perfectly fine.

*Note: I'm using 12.10 at the moment which is not considered stable yet. Should I just use the Stable release instead? I'm not a poweruser I just want wireless to work.

**TECHNICAL INFO**
Distro: Xubuntu-12.10-i386 (latest release)
Netbook: Dell Latitude | 2100
Wireless card (built-in): 0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Please be a nice cup of coffee and help me out

---

### Post by NikTh on 2012-10-26
Hi , 

Ubuntu 12.10 is considered a stable now , because released in [October 18th]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule") 

Although some bugs exists right now , because is a new release , we hope fixed soon. 

Can you provide some more info about your wireless ? 
Open a terminal (CTRL+ALT+T) and copy-paste from here bellow commands 
```
lspci -nnk | grep -iA2 net 
lsmod 
nmcli nm status 
sudo apt-get install jockey-common
jockey-text --list
```

Post back here the results and please put the results between the brackets **[noparse]```
the results here
```[/noparse]** so can be easy to read.
Thanks

---

