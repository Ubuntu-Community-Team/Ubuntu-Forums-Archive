---
title: "wireless problems with Intel 3945ABG"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Snakebit 001 on 2008-07-11
My wireless card worked when I first installed ubuntu, but then it stopped working. Apparently this is an issue related to the drivers and suspending the computer, and there are ways to fix it, but I'm very new to linux and haven't been able to follow the all of the instructions...
after using 'sudo /etc/init.d/hal restart' the computer started recognizing the wireless card but wireless still won't work.
```
$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
```
$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:9b:eb:e8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a
```
```
sudo lspci -vvv
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1010
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 00000000fee0300c  Data: 4142
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

I've gotten most of my information from [[color=blue]_bug 193970_[/color]](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970)
Apparently the wireless switch has to be off when you boot or resume from suspend (or something). To do that, I need to enable my 'rf kill switch' and I haven't been able to find instructions for enabling it that I can understand.
I am comfortable using the terminal, but I don't know most of the commands, or how to edit config files beyond opening them. Again, I'm new to linux and don't even understand all of the stuff I've posted; I just know that most of it's relevant

Please help!

---

### Post by jbrown96 on 2008-07-14
I have that wifi card and have never had any problems coming out of suspend. There is no reason why the card has to be deactivated; Linux automatically unloads all network drivers when it suspends. Does wlan0 show up when you ```
ifconfig
``` in a terminal? Is networking and/or wireless disabled in Network Manager (right click on the icon)? 
Try ```
iwlist scan
``` If that returns any results then your card is working, and the problem is with Network Manager.

---

### Post by timcredible on 2008-07-14
have you been doing system updates?  if so, you may have installed a new kernel.  to check, pick the old kernel at boot, see if wireless works.  if it does, then you need to add the wireless driver to the new kernel, or just always boot into the old kernel.

---

