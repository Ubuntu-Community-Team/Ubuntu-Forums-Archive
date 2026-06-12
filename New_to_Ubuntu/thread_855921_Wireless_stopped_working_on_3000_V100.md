---
title: "Wireless stopped working on 3000 V100"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Snakebit 001 on 2008-07-10
I have a Lenovo 3000 V100 with Ubuntu 8.04. My wireless worked 'out of the box' but recently stopped working. From what I can tell, the wireless card isn't being recognized. I've tried to research the issue, but I've only had ubuntu for a week now, so I've found the solutions very hard to follow.
Here is all the relevent information that I know of:
```
$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
```

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:20:ba:dc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=138.16.22.85 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

```
$ sudo lspci -vvv | less
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1010
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 220
        Region 0: Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0300c  Data: 413a
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <128ns, L1 <64us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
```

I have the i810 driver installed (I checked Synaptic).

I got the following message from the 'hardware testing' application that came with ubuntu:
```
Detecting your network controller(s):

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

$ sudo pccardctl ident
doesn't return anything

There are instructions on [_[color=blue]this page[/color]_](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check) and [_[color=blue]this page[/color]_](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-disabled) but I don't know how to do all of the steps...

Sometimes when I shut the computer down, the screen goes blank before going to the splash screen then fills up with text.

---

### Post by Snakebit 001 on 2008-07-11
bumping.
I added a lot of details to the original post. Sorry for the length (maybe the '-vvv' wasn't necessary...)

---

