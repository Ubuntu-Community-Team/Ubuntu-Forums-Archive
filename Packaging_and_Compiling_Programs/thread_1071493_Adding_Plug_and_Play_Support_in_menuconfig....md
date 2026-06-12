---
title: "Adding Plug and Play Support in menuconfig..."
date: 2009-02-16
forum: Packaging and Compiling Programs
---

### Post by vpnm_87 on 2009-02-16
Hi guys...

I am using linux 2.6.26..I chose 2.6.26/arch/arm/configs/at91sam9260ek_defconfig as my default config.....in that there is no Plug and Play Support...

normally its present in **device drivers-->Plug and Play support** when we give **make menuconfig**....

i checked that in my Ubuntu by issuing the same in /usr/src/linux directory....

can anybody tell me the steps to add new options like that in our default config selected..am terribly struck here..

---

### Post by geraldm on 2009-02-23
Plug N Play support was removed from the kernel.  See the kernel source Documentation/isapnp.txt  Documentation/pnp.txt
isa device information is now in sysfs file system, under /sys/bus/isa.

---

