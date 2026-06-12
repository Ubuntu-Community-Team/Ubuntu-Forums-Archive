---
title: "Error building kernel: .ko file format not recognized"
date: 2009-04-23
forum: Packaging and Compiling Programs
---

### Post by brooksbp on 2009-04-23
Downloaded kernel source... built with the cmd: AUTOBUILD=1 fakeroot debian/rules binary-debs

The first build worked just fine... was able to dpkg the build and boot the fresh kernel.  I tried to recompile again and ran into this problem:

[...]
  INSTALL drivers/ata/sata_via.ko
  INSTALL drivers/ata/sata_vsc.ko
  INSTALL drivers/atm/ambassador.ko
strip:/usr/src/ubuntu-intrepid/debian/linux-image-2.6.27-9-server//lib/modules/2.6.27-9-server/kernel/drivers/atm/ambassador.ko: File format not recognized
make[3]: *** [drivers/atm/ambassador.ko] Error 1
make[2]: *** [_modinst_] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory '/usr/src/ubuntu-intrepid'
make: *** [install-server] Error 2

I have NO idea why this would happen.  I didn't mess around with the source.  In fact, I probably don't need all these drivers.  I'm just doing a small kernel syscall hack.

Can anybody help!? Thanks!

---

