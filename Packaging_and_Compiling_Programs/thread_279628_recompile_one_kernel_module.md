---
title: "recompile one kernel module"
date: 2006-10-18
forum: Packaging and Compiling Programs
---

### Post by tormod on 2006-10-18
How can I rebuild just one kernel module, without building the whole kernel? I want to modify and rebuild a drm module.

I downloaded the kernel source package, made my build directory "mytree", copied in a .config, cd back to the kernel source, and ran:

make O=/home/tormod/kernel/mytree oldconfig
make O=/home/tormod/kernel/mytree drivers/char/drm/

And it successfully makes all the .o files. Then it stops, and complains about missing .mod files:
/bin/sh: .tmp_versions/drm.mod: No such file or directory
/bin/sh: .tmp_versions/tdfx.mod: No such file or directory
/bin/sh: .tmp_versions/r128.mod: No such file or directory
...

Anyone got a clue?
Thanks,
Tormod

---

### Post by tormod on 2006-10-18
I finally figured it out. I have to write it down anyway, so here it is:
```
apt-get source linux-image-2.6.15-27-386
# modify the source files I want to change

mkdir mytree
cp /boot/config-2.6.15-27-386 mytree/.config
cd linux-source-2.6.15-2.6.15
make O=../mytree outputmakefile
make O=../mytree archprepare
make O=../mytree modules SUBDIRS=scripts
make O=../mytree modules SUBDIRS=drivers/char/drm
```

Although I have the feeling this procedure is not the most correct one. There is some warning about missing versioning. And other SUBDIRS might have to be added for other modules.

---

### Post by tormod on 2007-05-13
I usually start with a ```
make O=../mytree oldconfig
``` after having copied the config file.

The version warning that I get is:
  *WARNING: Symbol version dump .../mytree/Module.symvers is missing; modules will have no dependencies and modversions.*

Does anyone have a clue how to easily get the Module.symvers generated? (Without having to compile the whole kernel or all the modules, that is.)

---

### Post by tormod on 2008-07-27
It's me again :) Copy the Module.symvers file from your linux-headers package first:```
cp /usr/src/linux-headers-2.6.24-20-generic/Module.symvers mytree/
```
And you might have to run```
make O=../mytree prepare
```

---

### Post by demonccc on 2011-01-11
Thanks man for the description that you give us. I could compile only one module instead all the kernel with you workaround.

---

