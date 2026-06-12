---
title: "wireless network problems since 'upgrade'"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by quercusrobur on 2008-10-22
Hi, last night I installed a backlog of updates to Ubuntu 8.06 using the update manager, ever since then I've been having great difficulty logging onto my wireless network. Previously I'd start up my laptop and automatically be logged onto my network. since the 'upgrade' a new icon has appeared in my panel, when there is no connection it shows a little image of a monitor with a red mark against it, when there is a connection it shows 4 little ascending bars going up like steps. Clicking on this icon will sometimes show me available networks in the area, sometimes it doesn't (ie, when it is having problems connecting). Hovering the curser over it shows signal strength.

Now when I want to log onto my connection I'm having to do this manually every time, including first having to type in my admin password then followed by typing in my 26 digit HEX key. Sometimes this works, sometimes it doesn't. Sometimes the panel icon disapears completely and it seems the only way to bring it back is to restart the computer and go through the whole process all over again.

This morning it has taken me about 20 minutes just to log onto my network in order to post this message, so any help or suggestions gratefully recieved! NB, prior to this have been using Ubuntu for 2 years with no wireless networking problems.

---

### Post by Nxion on 2008-10-23
> **quercusrobur said:**
> Hi, last night I installed a backlog of updates to Ubuntu 8.06 using the update manager, ever since then I've been having great difficulty logging onto my wireless network. Previously I'd start up my laptop and automatically be logged onto my network. since the 'upgrade' a new icon has appeared in my panel, when there is no connection it shows a little image of a monitor with a red mark against it, when there is a connection it shows 4 little ascending bars going up like steps. Clicking on this icon will sometimes show me available networks in the area, sometimes it doesn't (ie, when it is having problems connecting). Hovering the curser over it shows signal strength.

Now when I want to log onto my connection I'm having to do this manually every time, including first having to type in my admin password then followed by typing in my 26 digit HEX key. Sometimes this works, sometimes it doesn't. Sometimes the panel icon disapears completely and it seems the only way to bring it back is to restart the computer and go through the whole process all over again.

This morning it has taken me about 20 minutes just to log onto my network in order to post this message, so any help or suggestions gratefully recieved! NB, prior to this have been using Ubuntu for 2 years with no wireless networking problems.

Can you post the out put of this please. Lets see what wireless card you have. 

```
lspci
```

I found out that the latest kernel (2.6.24-21-generic) have been causing some headaches. after some reading, I guess some Nvidia video cards, Atheros based wireless cards and some Intel network cards have been the cuz of it.

---

### Post by quercusrobur on 2008-10-24
> **Nxion said:**
> Can you post the out put of this please. Lets see what wireless card you have. 

```
lspci
```

I found out that the latest kernel (2.6.24-21-generic) have been causing some headaches. after some reading, I guess some Nvidia video cards, Atheros based wireless cards and some Intel network cards have been the cuz of it.

lspci gives me;

graham@graham-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
graham@graham-laptop:~$

---

### Post by Nxion on 2008-10-26
Well if I am mistaken I don't see anywhere on there a listing of any wireless devices. So what is the make of the wireless card that you do have? What kinda of laptop do you have?

---

### Post by quercusrobur on 2008-10-26
As  far as I can tell its an Advent 7108 laptop

There's a sticker on it that says;
10/100/1000 Mbit LAN
WLAN 802.11 b/g

Does this help?

---

### Post by Nxion on 2008-10-27
Not really, Try this command:

```
lshw -C network
```


Also, does anything show up in System > Preferances > Hardware Drivers?

---

