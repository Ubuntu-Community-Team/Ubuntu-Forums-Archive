---
title: "build an external module from linux-backports-modules-alsa"
date: 2010-05-28
forum: Packaging and Compiling Programs
---

### Post by kenjiru on 2010-05-28
I've downloaded the sources with the following command:

```

sudo apt-get source linux-backports-modules-alsa-$(uname -r)

```

I've applied the patch I needed, but now I don't know how to build it as an external module.

```

radu@kenjiru:/media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda$  make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
make: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_analog.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_atihdmi.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_ca0110.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_cirrus.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_cmedia.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_conexant.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_sigmatel.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_intelhdmi.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_eld.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_nvhdmi.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_realtek.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_si3054.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/patch_via.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_codec.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_generic.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_proc.o
  CC [M]  /media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_hwdep.o
/media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_hwdep.c: In function ‘parse_hints’:
/media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_hwdep.c:435: error: implicit declaration of function ‘skip_spaces’
/media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_hwdep.c:435: warning: assignment makes pointer from integer without a cast
/media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_hwdep.c:450: warning: assignment makes pointer from integer without a cast
make[1]: *** [/media/work/temp/linux-backports-modules-2.6.32-2.6.32/updates/alsa-driver/alsa-kernel/pci/hda/hda_hwdep.o] Error 1

```

My guess is that I've supplied the wrong headers. But how can I tell it to look for the backports headers?

---

