---
title: "Wireless lan on Fujitsu Siemens - Amilo pi2540"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by xeNon XeO on 2008-11-24
Hey Guys,

I am completely new with Ubuntu as well as with Linux at all.
I have installed version 8.10 after reading a review :) I am of course coming from the MS OS :P

Now after reading hundreds of threads from people with the same issue, and read about madwifi and all the other hints tips and tricks, my WiFi is still reusing to work :(

As i said i am completely n00b on Linux, so most likely i did everything wrong myself :( Can somebody please help me with the install of either madwifi or .... anything that works ? Would be great !

Cheers and thanks in advance !

---

### Post by DieB on 2008-11-24
first of all try to get an wired connection, if that brings the conectivity, go to System-Administration-Hardware&drivers (for last I#m not sure due to other language setting). It should offer you to install a driver for that card.

If not post what "lspci" typed into an Terminal (Alt+F2 and type "gnome-terminal") spits out.

---

### Post by xeNon XeO on 2008-11-25
Cheers Mate :)

With the driver i've already tried but not working :( ( it says for Atheros cards there, and they are 2 :S )

The "lspci" i'll have to post it tonight for you, since i am on Gates *** again ;) Anyway thanks for the first help :)

---

### Post by xeNon XeO on 2008-11-25
```
xenon@xeNon:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
xenon@xeNon:~$ 

```

That's what the 'lspci' gives me :)

Hopefully you or somebody can help me :D

Btw forgot to say that the Lan 100 mbit is just working as it should do ;)

---

### Post by xeNon XeO on 2008-11-26
I have it working .... half ....

If i startup than go to system > administration > hardware drivers
than i see two types of Atheros drivers. One for the 5xxx series and one ... i think universal driver for Atheros cards.

If i switch of the first one, than switch on the second one and than switch on the first one again than i have wireless networking and i can connect to networks, as i am connected now.

Is there somebody who can tell me what to do so i don't have to do these steps every time ?

Many thanks if you know :)

---

