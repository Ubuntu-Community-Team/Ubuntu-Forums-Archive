---
title: "Graphics crash while playing games"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by libihero on 2013-06-02
When using Ubuntu 13.04, every once in a while while playing Counter Strike Source, everything would freeze and I would have to do a hard reboot. I thought it was something to do with compiz, and I was eyeing Kubuntu, so I decided to switch to that. When using Kubuntu, the same thing would happen, but this time everything would unfreeze after a few seconds and the everything was VERY laggy, from the game to KWin. I would have to log in and out again to fix it. For a while I thought it was just Counter Strike Source doing it, and maybe a bug in one of the maps, but today I was playing another game, Rochard, and the same exact thing happened. 

Here is the output for lspci:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
0c:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
0c:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)

```

Thanks :D

---

### Post by Autodave on 2013-06-02
Are you sure that you are not overheating the graphics chip?  Especially when you say that after is starts again, it is very laggy.  I am assuming that this is a desktop, so either try removing the cover and installing another cooilng fan, or if you don't have one available, just try a small fan blowing into the open case and see what happens.

---

### Post by libihero on 2013-06-02
This is actually a laptop, a Thinkpad E420. When a graphics chip overheats, is it permanently laggy until you log in and out? If yes, then that is probably what is going on :)

---

