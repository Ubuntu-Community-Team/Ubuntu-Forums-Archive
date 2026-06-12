---
title: "Wireless Networks listed as Unavailable"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by blindbaby on 2013-01-23
Hi, new user here, Thanks ahead of time for the help. I just did a fresh minimal install of Ubuntu 12.10. I then installed gdm, network-manager and gnome-core from tty. When I logged in, my wireless network was listed as unavailable in network settings and I'm not sure how to fix this issue. I'm using an AR928X Wireless Network Adapter (PCI-Express) in a Gateway NV-series laptop.

---

### Post by cariboo on 2013-01-24
Check in /etc/NetworkManager/NetworkManger.conf, it should look like this:

```
cariboo@alexis:/etc/NetworkManager$ cat NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
```

change the managed from false to true, and you should be could to go.

---

### Post by blindbaby on 2013-01-24
I made the changes to NetworkManager.conf as your suggestion and restarted my computer. When I logged in the first time and clicked on the upper taskbar's section for Network connections (I'm using GNOME 3) they all showed up, but after I entered the password and clicked "Authenticate" it said that it could not be completed and my Wireless Network section is again listed as unavailable.

---

### Post by squakie on 2013-01-25
Post back the output of:

lspci

We can look at that and see if there is a driver you may need also.

---

### Post by blindbaby on 2013-01-25
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] AMD RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by squakie on 2013-01-25
There are a LOT of posts on the net about this - try putting:

ubuntu 12 ar928x

in a net search string and read through those.  Unless someone has THE answer for you, I think we would just be searching through those ourselves.  Be sure to post back any questions, comments, etc., as I'm not blowing you off - it's just I would have to read those myself (and I suspect others as well) to try to find an answer for you.

cariboo907 is a VERY knowledgable person, so they may be able to help you more quickly than that, and more quickly than I could.  I wanted to be sure just exactly what we were dealing with.

---

### Post by blindbaby on 2013-01-25
Thanks, I'll start the search with that in mind.

---

### Post by blindbaby on 2013-01-25
The search didn't help too much, I wasn't able to find anything that helped with my issue specifically.

---

### Post by iMac71 on 2013-01-26
You might try what suggested in the following post:
[http://askubuntu.com/questions/220610/drivers-for-wifi-card-atheros-ar928x-find-and-install/221463#221463](http://askubuntu.com/questions/220610/drivers-for-wifi-card-atheros-ar928x-find-and-install/221463#221463)

---

