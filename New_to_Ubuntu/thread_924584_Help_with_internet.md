---
title: "Help with internet"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by lmworthen on 2008-09-19
I need help connecting to the internet. I'm running Ubuntu with Wubi and i cant find drivers for my Dell 1450 wireless card. Model Number:D1450U

---

### Post by mrtomservo on 2008-09-19
Not sure, but maybe this could be of some assistance! :)

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=908090]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=908090")

---

### Post by Bucky Ball on 2008-09-19
Could you copy and paste this into a terminal (Applications->accessories->Terminal):

**lspci**

Then paste the results back here. They actually use a Broadcom card in disguise!

---

### Post by lmworthen on 2008-09-19
i copied and pasted the command into terminal and it showed me a list of all my hadware excluding the wireless card and things like the keyboard, mouse and joystick. its actually a cisco card. it plugs into usb, not a pci slot on the mainboard.

---

### Post by lmworthen on 2008-09-19
madnessmaster23@madnessmaster23-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by Bucky Ball on 2008-09-19
In that case, can you plug it in and run that command again? Or plug it in and run this:

**lsusb**

---

### Post by lmworthen on 2008-09-19
Bus 005 Device 007: ID 06a3:0160 Saitek PLC 
Bus 005 Device 006: ID 04f9:0028 Brother Industries, Ltd 
Bus 005 Device 005: ID 413c:8104 Dell Computer Corp. 
Bus 005 Device 004: ID 050d:0413 Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 004: ID 06a3:8021 Saitek PLC 
Bus 001 Device 001: ID 0000:0000

---

### Post by lmworthen on 2008-09-19
it was plugged in the first time i tried it, but i tried the other command and came up with those results

---

### Post by Bucky Ball on 2008-09-19
[http://ph.ubuntuforums.com/showthread.php?p=5711479](http://ph.ubuntuforums.com/showthread.php?p=5711479)

This user seemed to get the device up by following the instructions on this page.

---

