---
title: "Newbie problem compiling acer_acpi"
date: 2005-12-12
forum: Packaging and Compiling Programs
---

### Post by rikoshay on 2005-12-12
Hi,

I'm a linux newbie (2 days old) switching over from microsoft. I installed the amd 64 version of breezy on my acer 5021WLMi and virtually everything's working apart from the broadcom wireless. After trawling around I've managed to find what I think is the missing link to get ndiswrapper to fire the card up - namely a program called acer-acpi. However when I try to compile it using the make command I get:

rik@lappy:~/Desktop/acer_acpi-0.3$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rik/Desktop/acer_acpi-0.3 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.12/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/rik/Desktop/acer_acpi-0.3/acer_acpi.o
  Building modules, stage 2.
  MODPOST
  CC      /home/rik/Desktop/acer_acpi-0.3/acer_acpi.mod.o
  LD [M]  /home/rik/Desktop/acer_acpi-0.3/acer_acpi.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'

I try make install but when I modprobe acer_acpi nothing happens. I presume it has something to do with the missing Module.symvers.

If anyone could enlighten me it would be appreciated.

Thanks

---

### Post by rikoshay on 2005-12-12
OK - so now I've managed to destroy my system whilst trying to get samba up and running on my home network. Anyway, I've reinstalled the amd64 ubuntu breezy and I'm left with the same problem. I've got the file acer_acpi-0.3.tar.gz. Can anyone give me an idiots guide on how to compile this and get it running?

---

