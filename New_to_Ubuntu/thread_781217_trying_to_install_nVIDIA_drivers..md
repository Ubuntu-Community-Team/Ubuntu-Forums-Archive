---
title: "trying to install nVIDIA drivers."
date: 2008-05-04
forum: New to Ubuntu
---

### Post by fignig on 2008-05-04
so i'm trying to install nVIDIA drivers and this is what my terminal looked like:

pete@pete:~$ sh NVIDIA-Linux-x86_64-169.12-pkg2.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 169.12............................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.

sh NVIDIA-Linux-x86_64-169.12-pkg2.run , was what i put in the terminal and it kept saying "ERROR: nvidia-installer must be run as root" 

not really sure what it's trying to tell me, can anyone help?

---

### Post by forestpixie on 2008-05-04
to run as root use sudo 

sudo *command*

It will ask for your password if you haven't used it yet - but it won't show up on screen, it is there though.

Have you not tried to install through Hardware Drivers in system >admin menu.

---

### Post by iSplicer on 2008-05-04
Just go to administration -> Drivers (or restricted driver manager) and enable the nvidia driver. That is the easiest way.

As to the problem that you are having, you need to run that command with "sudo" in front of it, so you can run it as root. So its

sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run

---

### Post by alienexplorers on 2008-05-04
Try running:
> sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run

---

### Post by fignig on 2008-05-04
> **iSplicer said:**
> Just go to administration -> Drivers (or restricted driver manager) and enable the nvidia driver. That is the easiest way.

As to the problem that you are having, you need to run that command with "sudo" in front of it, so you can run it as root. So its

sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run

okay it says it's enabled, how do i install sound drivers?

---

### Post by forestpixie on 2008-05-04
They should be installed - what sound card do you have - is Ubuntu recognising it? Run this in a terminal

```
lspci
```

---

### Post by fignig on 2008-05-04
> **forestpixie said:**
> They should be installed - what sound card do you have - is Ubuntu recognising it? Run this in a terminal

```
lspci
```

i did the lspci command and this is what i got:

pete@pete:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

---

