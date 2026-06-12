---
title: "Darkroom(KDE4) 1.3 not building in hardy"
date: 2009-09-24
forum: Packaging and Compiling Programs
---

### Post by seadao on 2009-09-24
I want to build darkroom(KDE4) 1.3 in ubuntu hardy, it's my favorite raw editor, but my computer can't run 9.04. so i installed all the dependences listed and stated cmake like the readme said

cmake -DCMAKE_INSTALL_PREFIX=$KDEDIRS -DCMAKE_BUILD_TYPE=debugfull .. 

i get this:

KDEDIRS -DCMAKE_BUILD_TYPE=debugfull ..
-- Found Qt-Version 4.4.0 (using /usr/bin/qmake-qt4)
-- Found X11: /usr/lib/libX11.so
-- Found Threads: TRUE
-- Found Perl: /usr/bin/perl
-- Found KDE 4.0 include dir: /usr/lib/kde4/include
-- Found KDE 4 library dir: /usr/lib/kde4/lib
-- Found KDE4 kconfig_compiler preprocessor: /usr/lib/kde4/bin/kconfig_compiler
-- Found KDE4 automoc: /usr/lib/kde4/bin/kde4automoc
-- Found PNG: /usr/lib/libpng.so
-- Found JPEG: /usr/lib/libjpeg.so
-- Check Kdcraw library in local sub-folder...
-- Check Kdcraw library using pkg-config...
-- Found libkdcaw release < 0.2.0, too old
CMake Error at /usr/lib/kde4/share/kde4/apps/cmake/modules/FindKdcraw.cmake:92 (message):
  Could NOT find libkdcraw header files
Call Stack (most recent call first):
  CMakeLists.txt:8 (find_package)


-- Configuring incomplete, errors occurred!

i installed libkderaw-dev
what's wrong, i need help please!

---

### Post by korin43 on 2009-09-29
Try installing libkdcraw7-dev from apt:
```
sudo aptitude install libkdcraw7-dev
```

If that doesn't work, try:
```
sudo apt-get build-dep darkroom
```
This will get all of the build depends.

---

### Post by seadao on 2009-11-01
the saga continues...

ok trying to build on hardy is an epic fail!! the libs are not in the repo, and i'm not that good with debian rules to risk killing synaptic with dodgy installs from source... (been through that before)

so i backed everything up and upgraded to 9.10 darkroom is in the repo, and it starts up fine. However when opening a raw file is crashes

the read out in the terminal is:

OpenCTL (Debug): in Program.cpp at 342 in OpenCTL::Program::init: Optimize
GTLCore (Debug): in Optimiser_p.cpp at 100 in GTLCore::Optimiser::Private::passManager: Finished pass manager
While deleting: float (float, float)* %powf
An asserting value handle still pointed to this value!
Aborted

is this a OpenCTL bug in 9.10??

so far it only worked for me in 9.04, but 9.04 kills my home folder after about three days so i can't use it (i tried every combination of filing system same result = home gets randomly deleted after a few boots)

so if anyone found a way to get darkroom to load a raw file in 9.10 or found a way to fix the home self destruction, please help

thank you for your time ubuntu gods!


NEW INFO!!
[https://bugs.launchpad.net/ubuntu/+source/darkroom/+bug/455165](https://bugs.launchpad.net/ubuntu/+source/darkroom/+bug/455165)

---

### Post by seadao on 2009-11-23
ok seems like ubuntu devs are abandening darkroom suppoert, as it says in the link of the previous post(or am i missing something).

however i have found a solution to the file syetem corruption in 9.04 in this thread... post #21

[https://bugs.launchpad.net/ubuntu/+bug/371191](https://bugs.launchpad.net/ubuntu/+bug/371191)

> Here's some info which may (or may not?) help track this down.

In the past 6 days, I've installed ubuntu jaunty 9.04 64bit on a new T500 laptop no less than 6 times. As others here report, I would start doing updates/upgrades, and shortly afterward would run into various issues which appear to all be symptoms of corrupted filesystem:

**** Faulty tree errors doing apt-get update
**** Errors about /var/lib/dpkg/status content
**** Errors about /var/lib/dpkg/info/something.list having blank lines

Then, at some point, dmesg would indicate that there was some ext3-fs or ext4-fs issue, and that journaling is aborted, and that the filesystem is remounted read-only, which would of course then cause all variety of desktop app misbehavior.

A coworker with another T500 that was shipped with mine, is experiencing the same issue on his hardware.

Another coworker with a T500, who got theirs in a different order, had been running Jaunty 64bit for a month now with no such problems, so we started to compare lspci output to see what chips might differ in the two T500's that would have one work solidly for a month while the other can't go 36 hours without corrupting its fs.

The only glaring difference we could see was that his laptop, which wasn't experiencing any problems, had a disk controller with device 20f8, using ahci driver, while mine was using the same model controller, but was listed with a device id 20f7, and which was controlled by ata_piix driver.

Working:

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
*Subsystem: Lenovo Device 20f8
*Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2298
*I/O ports at 1c40 [size=8]
*I/O ports at 1834 [size=4]
*I/O ports at 1838 [size=8]
*I/O ports at 1830 [size=4]
*I/O ports at 1c20 [size=32]
*Memory at fc226000 (32-bit, non-prefetchable) [size=2K]
*Capabilities: <access denied>
*Kernel driver in use: ahci

Failing:

00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
********Subsystem: Lenovo Device 20f7
********Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
********I/O ports at 01f0 [size=8]
********I/O ports at 03f4 [size=1]
********I/O ports at 0170 [size=8]
********I/O ports at 0374 [size=1]
********I/O ports at 1c20 [size=16]
********I/O ports at 1830 [size=16]
********Capabilities: [70] Power Management version 3
********Capabilities: [b0] PCIe advanced features <?>
********Kernel driver in use: ata_piix

I discovered that I could switch my disk controller device from 20f7 to 20f8, and use the ahci driver instead of ata_piix driver by going into my Bios settings, and under Config for the SATA controller, set it to "AHCI" instead of "compatible".

I'd suggest that compatible mode might have had issues, except from the amount of complaints here, it's just as likely that ata_piix is buggy when used on this hardware.

It'll be a couple days before I'm 100% comfortable that the issue is resolved for me, but I'm pretty sure switching the disk controller/behavior to match what has been working for other coworkers should account for the only difference between their hardware setup which hasn't run into this issue, and mine, which hadn't been able to escape it.

---

