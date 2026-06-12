---
title: "Screen brightness always minimum after boot."
date: 2012-06-03
forum: New to Ubuntu
---

### Post by r3bol on 2012-06-03
Hi, I recently installed ubuntu 12.04 on a laptop a friend gave me. It runs very well except that it always starts with the minimum brightness setting. I can adjust this by adjusting the level via the control pannel, but the setting reverts back to the mimium after every reboot. I thought this might have been fixed after a couple of updates, but it doesn't sem to be the case. How can I fix this? 

Here are my laptop specs...

Thanks. 

```
asdf@asdf:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1c30 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, fast devsel, latency 0
	Memory at fc100000 (64-bit, non-prefetchable) [disabled] [size=1M]
	Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fc406000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc406400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1830 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at 1c28 [size=8]
	I/O ports at 18fc [size=4]
	I/O ports at 1c20 [size=8]
	I/O ports at 18f8 [size=4]
	I/O ports at 1c00 [size=32]
	Memory at fc405000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Fujitsu Technology Solutions Device 1118
	Flags: medium devsel, IRQ 5
	Memory at 80000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c40 [size=32]
	Kernel modules: i2c-i801

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
	Subsystem: Fujitsu Technology Solutions Device 1117
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f8000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 3000 [size=256]
	[virtual] Expansion ROM at f2000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation PRO/Wireless 4965 AG or AGN
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fa000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwl4965
	Kernel modules: iwl4965

```

---

### Post by Redblade20XX on 2012-06-03
Take a look here: [https://wiki.archlinux.org/index.php/Laptop#Screen_brightness](https://wiki.archlinux.org/index.php/Laptop#Screen_brightness)

If the procedure that is given in the link works, you can look into creating a boot script that will set the brightness on startup!

-Red

---

### Post by r3bol on 2012-06-04
> **Redblade20XX said:**
> Take a look here: [https://wiki.archlinux.org/index.php/Laptop#Screen_brightness](https://wiki.archlinux.org/index.php/Laptop#Screen_brightness)

If the procedure that is given in the link works, you can look into creating a boot script that will set the brightness on startup!

-Red

Strange, the OS seems to recognise 2 different cards managing the brightness...
```
asdf@asdf:~$ ls /sys/class/backlight
acpi_video0  intel_backlight
asdf@asdf:~$ cat /sys/class/backlight/intel_backlight/brightness
0
asdf@asdf:~$ sudo echo "400" > /sys/class/backlight/intel_backlight/brightness
bash: /sys/class/backlight/intel_backlight/brightness: Permission denied
asdf@asdf:~$ cat /sys/class/backlight/intel_backlight/max_brightness
1

```
I tried to sudo change the /sys/class/backlight/intel_backlight/brightness (and max_brightness) and give it a an 8, but the OS refused to let me save the setting. 

What would you advise I change?

---

### Post by shakabra on 2012-06-04
Just add ```
acpi_backlight=vendor
``` to your grub kernel options. Don't forget to run ```
update-grub
``` afterwards.

---

### Post by r3bol on 2012-06-04
> **shakabra said:**
> Just add ```
acpi_backlight=vendor
``` to your grub kernel options. Don't forget to run ```
update-grub
``` afterwards.
Hi, I tried these steps, but it didn't work.

---

### Post by Pjotr123 on 2012-06-10
On my netbook, the solution to the same problem was changing a setting in the BIOS.

In that particular BIOS, in the Boot section, there is a setting called Brightness Mode Control. It was "Auto", and I changed it to "User Control". That worked fine. :)

---

### Post by Redblade20XX on 2012-06-10
> **r3bol said:**
> Strange, the OS seems to recognise 2 different cards managing the brightness...
```
asdf@asdf:~$ ls /sys/class/backlight
acpi_video0  intel_backlight
asdf@asdf:~$ cat /sys/class/backlight/intel_backlight/brightness
0
asdf@asdf:~$ sudo echo "400" > /sys/class/backlight/intel_backlight/brightness
bash: /sys/class/backlight/intel_backlight/brightness: Permission denied
asdf@asdf:~$ cat /sys/class/backlight/intel_backlight/max_brightness
1

```I tried to sudo change the /sys/class/backlight/intel_backlight/brightness (and max_brightness) and give it a an 8, but the OS refused to let me save the setting. 

What would you advise I change?

First when you change the values in the file "acpi_video0", did it automatically adjust the brightness?

-Red

---

### Post by r3bol on 2012-06-10
Hi, I don't have a brightness setting in my bios. 

> First when you change the values in the file "acpi_video0", did it automatically adjust the brightness?

-Red
I can't change (save) the brightness settings in the /sys/class/backlight/acpi_video0 folder. 

Some instances, it complains about not being able to save a backup, other instances it just refuses to save. 

I'm trying to edit them with sudo and gedit (if it makes a difference).

---

### Post by Pjotr123 on 2012-06-11
Try if this influences your screen brightness (use copy/paste to avoid typo's):
```

sudo setpci -s 00:02.0 F4.B=50

```

Press Enter. Enter your password when prompted. Your password remains entirely invisible, not even dots will show, this is normal.

Or, in case this doesn't work:
```

sudo setpci -s 00:02.1 F4.B=50

```

Experiment with other values than 50.

In case it works, make it persistent:

First install text editor Leafpad, which is better suited for this kind of jobs than the default Gedit. Then:

```

gksudo leafpad /etc/rc.local

```

Add above exit O :
```

setpci -s 00:02.0 F4.B=50
(or setpci -s 00:02.1 F4.B=50)

```

The text then should look like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
setpci -s 00:02.0 F4.B=50
exit 0

```

Reboot. The brightness should now be at an acceptable level automatically.

---

### Post by r3bol on 2012-06-11
> sudo setpci -s 00:02.0 F4.B=50

sudo setpci -s 00:02.1 F4.B=50

Neither worked :(

---

