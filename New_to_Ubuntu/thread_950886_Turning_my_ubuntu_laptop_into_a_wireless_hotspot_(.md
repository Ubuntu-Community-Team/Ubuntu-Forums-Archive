---
title: "Turning my ubuntu laptop into a wireless hotspot (bump)"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by shabs on 2008-10-17
BUMP
Hi,
I'm running ubuntu 8.04 and I have a built-in wireless card. I would like to let my friend (running vista) access internet from my laptop. I'm connected to a wired connection. How can I do that?
In netowrk manager there is an option that says "Create New Wireless Network", when clicked it asks me to enter a network name and gives me options for wireless security. Once thats entered I network manager icon starts revolving around like its trying to connect to a network and then nothing happens. My friend still does not see my network in his list of wireless networks. Roaming mode is enabled.

---

### Post by LowSky on 2008-10-17
for windows and Linux to even see one another you need a few things installed like Samba and i think you might neeed LAMP, not sure?

take a look at this guide I found doing a google search
[http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html](http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html)

---

### Post by shabs on 2008-10-17
Hi Lowsky, thanks for your reply. I find the guide a bit complicated. I assumed it would be simple in linux to let my friend connect to me wirelessly with me connected to a wired connection. I will eventually have to try this, but till then I'm hoping someone has a simpler and shorter solution.

---

### Post by LowSky on 2008-10-17
Welcome, for the most part you will need samba, that I know, easily installed form add/remove, also open up the network connection tool (on the top panel bar, and see if it has an option for direct connection to another PC, I would do it myself but I'm at work and using a Windows machine.

---

### Post by shabs on 2008-10-17
The network connection tool that you're talking about, well I have NetworkManager and when clicked it lists out an option that says Create New Wireless Network. Whats that for?

---

### Post by Pconfig on 2008-10-17
Take a look here.

Perfect guide :) Samba doesn't really have to do anything with this. With samba you can share files with a windows box. He's trying to setup an access point so another computer can connect with his computer.

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

---

### Post by shabs on 2008-10-17
Thanks for the link Pconfig, it talks about using an Atheros card with madwifi. I have a realtek and I use NetworkManager. Also the last time I tried to put my card in Master mode it didn't work. At this point I'm not sure if that guide is for me. What do you think? Heres the output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Pconfig on 2008-10-17
Woops, that was wrong indeed. You need to get an adhoc network?

Well, you're on the right track.
Take a look here. It explains how you should create one. I think you're doing it right.

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by linux6994 on 2008-10-17
Why not just get a wireless router (Linksys, Netgear or D-Link) then you both can play untethered.

---

### Post by shabs on 2008-10-17
Hey again,
You're right pconfig, I guess what I need is a ad-hoc network, I wasn't asking the right question I suppose.
I tried this 
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
substituting wlan0 as my wireless interface but it still wont put my card into ad-hoc mode. And the vista laptop won't bring up my network in its list of available wireless networks.
Any other ideas? :)

---

