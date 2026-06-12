---
title: "UBUNTU 14.04.2 LTS problems with HP wireless printer"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by Tomfilery on 2015-03-25
Hi,

I've successfully managed to get Ubuntu to dual boot with Windows 8.1 on my Sony VAIO laptop (type SVE1513B4E) and all seems to be working pretty well, however, I just can't work out how to get my system to print to my HP Photosmart C7280.  The main problems are that I simply don't know what I actually need to load to get it all to hackle!

I found a Wiki page [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne) which provided details of the HPlip software and successfully ran that, got all the missing pieces of software loaded, but my system simply can't find my printer on the network.  I've tried putting in the printer's URL and the router's URL but all to no avail. Doubtless there is some really simple instruction which I've neglected to insert/load.  A lot of the guides assume you know where to find all the data you need (e.g. the URI for a local printer), but frankly, being new to all of this I just don't have clue.

The printer does function when used from Windows and will need to be accesssed by one other user (who doesn't use Ubuntu).  Can someone please point me in the right direction?  I've searched for other threads with similar issues, but feel I've pretty much exhausted all the leads they've given me without success.

Regards Tom

---

### Post by DuckHook on 2015-03-25
Welcome to Ubuntu and the forums!

Print out your printer settings. This is usually shown on your printer's test page. Note the IP address. Then, open a terminal and:```
hp-setup
```...which will bring up the HP Device Manager. Select the "Network/Ethernet/Wireless network">Next. Look for the printer with your IP address. If none shown, click refresh.

If above does not work, click <Back> button. At "Device Discovery" box: select Show Advanced Options>Manual Discovery and type in the IP address of your printer. Click <Next>. Select your printer on the next screen and follow remaining instructions to complete installation.

---

### Post by Tomfilery on 2015-03-26
DuckHook,

Many thanks - thought it would be something simple but I didn't know where to look.  The HP program found the printer straight away - something I'd been unable to get it do for some reason the other times I tried!

Your assistance greatly appreciated.

Regards Tom

---

### Post by DuckHook on 2015-03-26
> **Tomfilery said:**
> ...I didn't know where to look.  The HP program found the printer straight away - something I'd been unable to get it do for some reason the other times I tried!

Your assistance greatly appreciated...Glad to help. Sometimes this stuff is like sorcery and successful discovery of the printer depends on things that are way beyond me like network topology issues, router type, switches, network segmentation, etc. What I've found is that you can usually force your computer to find the printer by manually searching for its IP address.

I forgot to mention that it is very important to set your printer to a static IP address. This is usually done on your router, or whatever box you are using as your DHCP server. You don't want your printer being reassigned another IP, which would break your network printing.

Good luck and Happy Ubuntuing!

---

