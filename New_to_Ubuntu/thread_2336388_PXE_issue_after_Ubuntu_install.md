---
title: "PXE issue after Ubuntu install"
date: 2016-09-07
forum: New to Ubuntu
---

### Post by mikeperreman on 2016-09-07
ok, i will preface this with, i am completely new to Ubuntu, the only previous experience is with the raspberry pi, so, its safe to say that im an idiot, so dont take anything for granted when answering, basically, here is my problem, and what i did, so, i took a hard drive out of a laptop, scanned for errors (faults, bad sectors, that kind of thing) and installed Ubuntu. it all went well, no errors, however, when i rebooted after install, and before the bios/manufacture start splash turned on, (that dead period before the screen turned off, but after the fan was powered off), and goes through normal boot, then i get a:

PXE-E61 Media test failure, check cable

PXE-MOF Exiting PXE ROM


then it reboots into the boot device select screen, at this point, if i were to plug in the flash and select the hdd, it just blackscreens, if i plug in the flash and boot it(after a hard shutdown) it boots into grub, where i have the options to 1) Try Ubuntu, 2) install Ubuntu, 3) OEM install, 4) check disk for errors. it (the screen that it boots to) is titled gnu grub version 2.02. plz halp, i am out of ideas. thanks for helping me out. :)

for the general info, im attempting to install version 16, whatever the current one is as of 7/9/16

---

### Post by QIII on 2016-09-07
Hello!

Let's do the obvious first and check the cables on the disk.  Check both ends of the SATA cable.

Cheers!

---

### Post by mikeperreman on 2016-09-07
yes, im sorry for not specifying, but i am running a lenovo laptop

---

### Post by mikeperreman on 2016-09-07
ok, so i decided, just for the hell of it, i mind as well prove to myself that the computer works and hdd works, so i installed windows to the hdd, and the thing boots right up, no problems, so is there a possible bootloader that inst installed to the hard drive, or what?

---

