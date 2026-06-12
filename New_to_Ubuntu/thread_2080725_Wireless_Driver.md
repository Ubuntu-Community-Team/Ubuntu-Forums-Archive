---
title: "Wireless Driver"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by philpense on 2012-11-04
see an option to identify my wireless adapter (internal).  Must I boot up in windows xp and get identifying information or is there a  sophisticated way to do so/  Guidance sought

---

### Post by duanedesign on 2012-11-04
To determine what wireless card/chipset you have, first determine whether it is a separate device plugged into the computer or not. If it is a separate USB device, open up a terminal and type the following:

```
lsusb
```
and look for words like "wireless" to find your card type.

For chips that are not USB but included in the computer, type:

```
lspci -v
```
and read the last section. [1]



[B]Quick Check
[/B]With your computer turned off, insert your wireless adapter into a suitable port/slot.
Turn on your computer and log-in if/when prompted.
Open a terminal window and enter the following command:
```
nm-tool
```
This program will output the information Network Manager has collected about your card, much of which will assist in setting-up wireless networking .
If the output contains:
```
State: connected
```
(and you are not on a wired connection) then your wireless adpater is working and connected to a network.
Left-click on the panel applet (four vertical bars in 9.10 or older; 4 concentric arcs in 10.04). If you can see wireless networks, then your wireless works; you need to connect to a network. See below on network connection.[1]

Hope these help.

[1] [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[2] [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by NikTh on 2012-11-05
Hi , 
please boot to Ubuntu , open a terminal (with CTRL+ALT+T) and copy-paste from here bellow commands, one line at time.
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list all
lsb_release -rcd ; uname -r 
sudo fdisk -l
``` 

Copy-paste the results back here and place the results between the brackets ==>[noparse]```
the results here
```[/noparse]<== to be easier to read. 
Results should appear in ```
here
```

Thanks

---

### Post by squakie on 2012-11-05
Nikth has it pretty much covered.  I just wanted to add a small "correction" to duanedesign's reply:

No matter if the adapter is internal or external, it's best to do both the lsusb and lspci.  Reason?  There are laptops out there (and maybe motherboards) whose internal wireless is actually connected on the usb bus.  So while it may be internal, it may still be usb.

---

### Post by philpense on 2012-11-06
Much thanks for the timely reply. wireless module is built into the system board but I have yet to find how one summons the "terminal"?  Continued guidance sought

---

### Post by philpense on 2012-11-06
Appreciate the assistance.  I got this return from a simpler query.

this@this:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 82d9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 82d9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 82d9
	Flags: bus master, fast devsel, latency 0
	Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 8337
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 7f900000-7fafffff
	Prefetchable memory behind bridge: 000000007fb00000-000000007fcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 000000007fd00000-000000007fefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7eb7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: bus master, medium devsel, latency 0
	Kernel modules: lpc_ich, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device 82d8
	Flags: medium devsel
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

03:00.0 Ethernet controller: Atheros Communications Inc. L2 Fast Ethernet (rev a0)
	Subsystem: ASUSTeK Computer Inc. Device 8233
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at fbfa0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: atl2
	Kernel modules: atl2

this@this:~$ 

I will use your command suggestion if this is not sufficient.

---

### Post by varunendra on 2012-11-07
philpense,
There is no wireless device listed in your lspci output. If you are sure it is connected,  then either it is indeed on a usb bus as *squakie* mentioned, or it is disabled in BIOS. Accordingly, make sure it is enabled in BIOS, then post the outputs of commands asked by *NikTh*.

Or even better, just run the following command (simply copy-paste it in a terminal) :
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download and run a script that will collect all relevant info and dump it to a file named "netinfo.txt" in your 'Home' directory. Open that file and copy-paste its contents here in your new post (paste it between **'code'** tags generated by clicking on **#** at the top of the edit box in which you create new posts).

@NikTh,
I couldn't understand the relevancy of *fdisk* here. What are you trying to figure out by its output ? Just curious :)

---

