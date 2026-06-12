---
title: "Compile Path?"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by Mikesla on 2011-11-14
I am being asked while setting up a config where the compiler is.

 I need to know if this is the correct path, it's telling me this but when I say to compile it's telling me I need a compiler installed. I have installed everything there is to install.

Here is what it defaults to when asking...

[/lib/modules/3.0.0-13-generic/build]

But when I press enter I get this error.

 > driver version 1.21full
(cd /lib/modules/3.0.0-12-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-12-generic/build" "M=/usr/lib/hcfpcimodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciosspec.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciserial.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciengine.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpcihw.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.0.0-12-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-12-generic/build" "M=/usr/lib/hcfpcimodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_engine.o
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_hcfpci.o
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_osspec.o
In file included from /usr/lib/hcfpcimodem/modules/mod_osspec.c:323:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
In file included from /usr/lib/hcfpcimodem/modules/mod_osspec.c:323:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
  CC [M]  /usr/lib/hcfpcimodem/modules/osservices.o
In file included from /usr/lib/hcfpcimodem/modules/osservices.c:20:0:
/usr/lib/hcfpcimodem/modules/GPL/oscompat.h:201:57: error: ‘SPIN_LOCK_UNLOCKED’ undeclared here (not in a function)
In file included from /usr/lib/hcfpcimodem/modules/osservices.c:44:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
/usr/lib/hcfpcimodem/modules/osservices.c:51:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/lib/hcfpcimodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hcfpcimodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [all] Error 2


Like I said I have downloaded everything there is to download. So if I need a compiler where can I get it?

---

### Post by jtarin on 2011-11-14
What are you trying to compile?

---

### Post by Mikesla on 2011-11-15
> **jtarin said:**
> What are you trying to compile?

I'm trying to install a HCF modem driver (dialup).

---

### Post by MG&amp;TL on 2011-11-15
From what I can see, you need gcc:

```
sudo apt-get install gcc
```

then specify /usr/bin/gcc as the path to compiler. Unless you've done something unusual.

---

### Post by Mikesla on 2011-11-16
> **MG&TL said:**
> From what I can see, you need gcc:

```
sudo apt-get install gcc
```then specify /usr/bin/gcc as the path to compiler. Unless you've done something unusual.

Thanks for the reply.

 I have the latest gcc installed.

 When I do enter the path you have gievn me I am recieving this error.

WARNING: missing file /usr/bin/gcc/include/linux/autoconf.h

Should I be coping over autoconf.h to the linux directory?

Thanks.

---

### Post by jtarin on 2011-11-16
> **Mikesla said:**
> I'm trying to install a HCF modem driver (dialup).Are you compiling the latest modem driver for your modem? Where did you download from? Are you sure its the correct driver?
From what I understand at kernel 2.6.33, the file name changed from linux/autoconf.h to generated/autoconf.h., so I would try to get the latest driver for your kernel....which is probably later than 2.6.33.....I'm guessing.

---

