---
title: "Broadcom chip detected. No link"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by smalltowndoc on 2008-05-10
I am new to Ubuntu (Kubuntu 7.1). Installed it 2d before. Laptop Acer 4720Z. Wireless chip was not detected. Tried Ndiswrapper website and found Atheros 5006 as my chip [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/").
Mistake. I found after three hours of meddling and getting a wrist pain, that my lappie has Broadcom chip. Which i got it installed. Now the problem is, when i put iwconfig, i get the chip detected as eth1 (eth 0 as wired LAN, i guess). The signal strength is some 250db but link show as 0. Sometimes i get the message the network address i am giving is wrong. I love Kubuntu. except for the difficulty in getting this wireless connection and no sound. Thanks in advance for reading this. I am greatful if some one can help.

---

### Post by DrPppr242 on 2008-05-10
You might make sure your on the network and not just authenticated against the wireless.  iwconfig will join the wireless but with running a dhcp client there's no network connectivity.

---

### Post by smalltowndoc on 2008-05-10
Thanks a lot DrPppr242. That was lightning fast. Being very new to Ubuntu. I do not very well understand what you replied. It shows that there is signal and zero noise (Iam sitting right next to the wireless modem/router) but there is no link. That means i guess it is detecting the signals but not being connected. I removed the WEP code in the router so that, it will not cause trouble. I am sorry if my question is not coherent. I wish i could be

---

### Post by DrPppr242 on 2008-05-10
Are you trying to connect using the terminal or using the graphical utility? if the gui tool doesn't work open a terminal and try 'sudo iwlist eth1 scanning' if that displays the available networks your card should be working.  Next 'sudo iwconfig eth1 essid *network name* key *wep key*' should connect to the AP, leave off the key part if there's no security, then 'dhcpcd eth1' or 'dhclient eth1' depending on what's on your system will get an IP address.

---

### Post by smalltowndoc on 2008-05-10
When i scan for networks using terminal no networks are picked up. I am using GUI because i do not know anything about terminal except the commands i read here & there. Thanks again for your interest. You are making me understand Ubuntu, helping others.

---

