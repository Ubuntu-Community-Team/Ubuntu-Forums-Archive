---
title: "Cannot Connect to Wifi"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by smb140p on 2012-08-05
Hi guys,

I just installed Ubuntu 10.04 on my HP Mini 110 netbook (via Wubi installer) and I found I cannot connect to wifi, whether the hardware button is on or not.

I entered lspci in the terminal and got this:

```

hanchennn@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

```Do I have to download drivers for my wifi card? If I do, where do I get it from, and how do I set it up?

---

### Post by yeats on 2012-08-05
This link should help you:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by levlaz on 2012-08-05
Is there a physical button on your laptop that turns the wifi on/off? I had this happen on an old Thinkpad and was confused for hours until I thought to turn it on. 

Also your wireless card may be turned off in the BIOS as well you could check that too. (reboot the computer and the first screen should say something like "F2 for setup" )

---

### Post by smb140p on 2012-08-06
That fixed the problem, thanks. But now for some reason the battery indicator doesn't show up unless I plug it in to charge, and when I unplug and restart, it disappears again...

---

### Post by ironnerd88 on 2012-08-06
[FONT="Courier New"]smb140p - I'm so glad you posted this!

I installed Ubuntu 12.XX desktop on my HP Mini 110-1144NR last night. Most of it works great and is already an improvement over Win 7 starter (which is saying something because I actually like Win 7). Like you (and many others installing on a Mini 110) I have no network connection, even with the wire plugged in. Network adapter light is on (blue, not orange), but I get nothing. I'll follow the link above, and report back.

Thanks to all![/FONT]

---

### Post by little_penguin on 2012-08-06
For the battery icon, check System -> Administration -> Power management -> General tab
and check that "Always display an icon" is selected.

---

### Post by wildmanne39 on 2012-08-06
Please mark this thread solved by using thread tools at the top of the page and start a new one if you need more help with the new issue.
Thanks

---

