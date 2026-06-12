---
title: "Cannot boot: 'Start job is running for udev Coldplug all devices' with no limit"
date: 2019-05-25
forum: New to Ubuntu
---

### Post by t.bermejo on 2019-05-25
This is my first time installing Ubuntu and I am trying to get it running with dual boot alongside Windows 10 on my HP Envy 15-ah150sa laptop.


After getting around some problems I managed to install Ubuntu 18.04 (linux image 4.15.0-50-generic) from a UEFI USB drive. But now I'm having problems booting into Ubuntu.


Right after choosing 'Ubuntu' at the GRUB menu, I see a short sequence of 'OK' tasks and then everything stops as two tasks hang. The messages are:


1) [FONT=courier new]A start job is running for dev-disk-by\x2uuid-81AC\xdE0D1.device (12s / 1min 30s)[/FONT]
2) [FONT=courier new]A start job is running for udev Coldplug all devices (12s / no limit)[/FONT]


Once task 1) times out, the system drops into Emergency Mode and I'm able to use a shell.


As a bit of a guess after some googling, I commented out the drive mentioned in 1) in [FONT=courier new]/etc/fstab[/FONT] and that did seem to solve that problem. The result is actually worse though, because that leaves with just 2) hanging indefinitely, and since there is nothing to time out I no longer get to Emergency Mode, so I'm pretty much powerless (the same happens if I try to boot in recover mode from GRUB). In the end I've reinstalled from the USB drive, so now I'm back to the two errors but at least I can get an emergency mode shell. 


The weirdest thing is that very occasionally (twice in the 20-30 times I've tried to boot), the udev coldplug task doesn't appear and I've been able to boot just fine. Frustratingly I can't think of anything at all that might have been different in those cases to make it work. And then when I then shutdown the same old hanging message appears again and I have to hold down the power button to power off.


I can't find anything useful online about the udev hanging task. Can anyone shed some light on what it is that might be failing and how I can try to get round it?


P.S. just in case this might be relevant: when I was installing from the USB drive, at first I couldn't launch the Ubuntu installer as
freedesktop.upower.org would fail. In the end I added a line to [FONT=courier new]/usr/lib/ubiquity/ubiquity/upower.py[/FONT] that bypasses a check to see whether the machine has a battery, avoiding the error. Perhaps this is in some way related?

---

