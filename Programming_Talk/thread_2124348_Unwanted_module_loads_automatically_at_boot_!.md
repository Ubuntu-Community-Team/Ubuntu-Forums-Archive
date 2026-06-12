---
title: "Unwanted module loads automatically at boot !"
date: 2013-03-10
forum: Programming Talk
---

### Post by jsteele22 on 2013-03-10
Ubuntu 12.04 LTS ,   3.5.0-23-generic kernel,  x86_64

I have been developing some modules for my system, and for some reason one of them re-loads automatically at boot-time.

symptoms :

1) modprobe mesa_5i23 # that's my module
2) shutdown -h 0
3) (power off)
4) (power on)
5) lsmod | grep mesa_5i23 # yes it is there !

The module is *NOT* listed in /etc/modules.

I've been coding kernel modules for many years, and all my understanding is that this should *NOT* happen !  What's going on ?

Possible contributing factors :

The module installs a PCI driver (a first for me)
I'm brand new to Ubuntu.

A dmesg after reboot shows the following. (The bold part is produced by my module)

```

[    2.634910] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).[    2.634916] [drm] Driver supports precise vblank timestamp query.
[    2.666967] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.674737] usbcore: registered new interface driver usbhid
[    2.674747] usbhid: USB HID core driver
[    2.681249] type=1400 audit(1362945120.877:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=382 comm="appa\
rmor_parser"
[    2.682910] type=1400 audit(1362945120.877:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-cl\
ient.action" pid=382 comm="apparmor_parser"
[    2.683868] type=1400 audit(1362945120.877:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-\
script" pid=382 comm="apparmor_parser"
[    2.716152] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    2.724929] [drm] GMBUS [i915 gmbus panel] timed out, falling back to bit banging on pin 3
[    2.740864] i915: fixme: max PWM is zero
[    2.741652] lp0: using parport0 (interrupt-driven).
[B]
[    2.745952] Mesa Anything I/O driver installed
[    2.746018] mesa_5i23 0000:05:00.0: enabling device (0010 -> 0013)
[    2.746088] ERROR: invalid FPGA config ID : 0x00000104
[    2.746102] Mesa 5i23 not fully probed
[    2.746116] mesa_5i23: probe of 0000:05:00.0 failed with error -5
[/B]
[    2.752328] [drm] initialized overlay support
[    2.826338] microcode: CPU0 sig=0x106ca, pf=0x8, revision=0x107
[    2.899639] usb 5-2: New USB device found, idVendor=046d, idProduct=c52b
[    2.899652] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.899660] usb 5-2: Product: USB Receiver
[    2.899667] usb 5-2: Manufacturer: Logitech
[    3.019272] fbcon: inteldrmfb (fb0) is primary device
[    3.021266] Console: switching to colour frame buffer device 160x50
[    3.021359] fb0: inteldrmfb frame buffer device
[    3.021366] drm: registered panic notifier
[    3.021406] i915: No ACPI video bus found
[    3.021653] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.022501] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \_SB_.PCI0.GFX0.TCOI 1 (20120320/ut\
address-251)
[    3.022526] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.022533] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    3.022543] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPE0 1 (20120320/utaddress-251)

```

As far as installation, I copy the module to :

/lib/modules-3.5.0-23-generic/extras/

I add that dir to my depmod search path ( add file : depmod.d/extra.conf) and run depmod.

I set up some modprobe rules in /etc/modprobe.d/mesa.conf ( install mesa_5i23 ...)



Note that the module loads correctly when I run modprobe mesa_5i23 from the command line.  But the (unwanted !) auto-load at boot time fails; this indicates to me that it is being loaded by an insmod command and not modprobe : the modprobe rules are being ignored.

---

### Post by jsteele22 on 2013-03-11
Okay, I got it figured out.

The module is being loaded by the hotplug mechanism.

Because the module registers a PCI driver, when depmod runs it keeps a record of this in /lib/modules/xxx/modules.alias .  Anytime the system detects new (unknown) hardware, the udev daemon checks this file to find a module that provides a driver.

I suppose this is a good thing, but it sure is a nuisance when that is *not* the behavior you want/expect.

Perhaps some of the kernel module programming documentation out there could stand to be corrected :

1) If you want a module to load at boot-time, list it in /etc/modules OR REGISTER A DRIVER.

2) The function pci_register_driver() tells the system that you are ready to handle a particular device, BUT THE SYSTEM ALREADY KNOWS THAT BEFORE YOUR CODE IS EVEN EXECUTED.

Sorry for sounding grumpy.  It's just that I'm feeling pretty grumpy.  Have a nice day.

---

