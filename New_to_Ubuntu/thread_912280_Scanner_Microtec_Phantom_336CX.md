---
title: "Scanner Microtec Phantom 336CX"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by ulindel on 2008-09-06
Trying to use my "Scanner Microtec Phantom 336CX" in ubuntu?

Its CD will not run in ubuntu.

I run " XSane Image Scanner" in ubuntu, which is supposed to use any flatbed scanner, but says" no devices available".

thanx nick

---

### Post by forger on 2008-09-06
The company is "Microte_k_", not "Microte_c_"

1) Try this in terminal (Applications > Accessories > Terminal):
```
sudo apt-get install sane-utils
sudo adduser $USER scanner
```
2) Then log out and log in (or simply reboot your computer)
3) When you log in again, execute this in terminal:
```
scanimage -L
sudo sane-find-scanner
sane-find-scanner
```

Post a reply with the full output of step 3.
Logically, it should work now and find the scanner.

**If it didn't find the scanner**, post the reply of these commands:
```

lsusb
lspci
dmesg | tail -n 40

```
( More info: [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo) )

---

### Post by forger on 2008-09-06
Are you sure it's Phantom 336CX ? Please check the brand/model again.
I'm asking in case it's not supported, because there are some microtek devices that are not supported:
[http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK](http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK)

---

### Post by 24T on 2008-11-09
Hi,
on my side step 3 gives :
```
found SCSI scanner "  scanner 330CSU 1.31" at /dev/sg2
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

found USB scanner (vendor=0x05da, product=0x00a0) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```
The scanner remains unrecognized ! What to do next ?

---

### Post by alienexplorers on 2008-11-09
The 336CX is probably detected as a 330CX under the microtek2 backend. It should be completely enabled for Ubuntu.

---

### Post by 24T on 2008-11-11
Sorry, but it's not straight forward for me.
```

pic@x64:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

pic@x64:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 (rev a2)

pic@x64:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 026: ID 05da:00a0 Microtek International, Inc. Phantom 336CX/C3 (#2)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo scanimage -d microtek2:/dev/sg2 --mode Color > myscan

```

About one minute later, system freezes (no more Ctrl-Alt-Fn), and I have to power-off the machine

I have read an old similar case :
> 
Subject: 	Re: microtek slimscan c3 freezes system

On Wednesday 28 September 2005 20:00, w kay wrote:
> I'm using Libranet gnu/linux 3.0 & recompiled the kernel to include the
>    linux-ppscsi-2.6.x.patch.gz, which succeeded in the microtek slimscan
> c3 scanner being detected by -xsane, xscanimage,quiteinsane-But when I
> try to scan using any of these, the system freezes up totally & I have
> to reboot. I would be interested to know if anyone here has used this
> scanner successfully & any ideas to get it working. my machine is:
>
> e machines T2080
> AMD Athlon 2000+
> 512 MB ram
>
> Let me know if I can ginve any other info. Thanks,


Don't know if related but these mod's are missing : ppscsi epst

Thanks for help

---

