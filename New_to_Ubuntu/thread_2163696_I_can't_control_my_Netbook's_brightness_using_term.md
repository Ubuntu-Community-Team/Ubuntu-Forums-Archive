---
title: "I can't control my Netbook's brightness using terminal"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by mr.akik on 2013-07-19
I'm trying to control my Netbook's brightness using terminal.
This is the output of "ls /sys/class/backlight" command:


intel_backlight


Here's the output of "sudo lspci -vnn | grep -A10 VGA" command:


00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device [8086:a001]
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at f0300000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 18d0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915


I've tried this:
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
This:
xbacklight -set 50
This:
sudo setpci -s 00:02.0 F4.B=7f
All these give no output message.
I added "acpi_backlight=vendor" to kernel paramiter.
But nothing worked. Please help

---

### Post by dino99 on 2013-07-19
which brand is it ? some need additional package(s) installation (glance at synaptic about that brand)

---

### Post by mr.akik on 2013-07-19
> **dino99 said:**
> which brand is it ? some need additional package(s) installation (glance at synaptic about that brand)
It's name is "Doel",No brand. It's made in china.

---

### Post by mr.akik on 2013-07-19
please help

---

### Post by DeathByDenim on 2013-07-19
In addition to the parameter "acpi_backlight=vendor", could you also add "acpi_osi=Linux"? (without the quotes)

Also, what does this say?
```
cat /sys/class/backlight/intel_backlight/brightness
```

---

