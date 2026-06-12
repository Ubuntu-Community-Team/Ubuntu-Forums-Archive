---
title: "qemu configure error"
date: 2006-03-08
forum: Programming Talk
---

### Post by carverj on 2006-03-08
am trying to configure qemu and it doesn't like gcc 4.x

```
jeremy@UBUNTU:~/temp/qemu-0.8.0$ ./configure gcc 3.3
ERROR: "gcc" looks like gcc 4.x
QEMU is known to have problems when compiled with gcc 4.x
It is recommended that you use gcc 3.x to build QEMU
To use this compiler anyway, configure with --disable-gcc-check

```

Should I remove gcc 4.x ? because a few programs seem to be dependant on it!
:-? 
Thanks guys/gals

---

### Post by swamytk on 2006-03-08
Better install gcc 3.x also. It is available in ubuntu repository. It is useful for any driver related compilation.

---

### Post by carverj on 2006-03-08
can someone tell me if this is how the make is supposed to end or do I still have problems?

>  Building modules, stage 2.
  MODPOST
Warning: could not find /home/jeremy/temp/qemu-0.8.0/kqemu/.kqemu-mod.o.cmd for /home/jeremy/temp/qemu-0.8.0/kqemu/kqemu-mod.o
  CC      /home/jeremy/temp/qemu-0.8.0/kqemu/kqemu.mod.o
  LD [M]  /home/jeremy/temp/qemu-0.8.0/kqemu/kqemu.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/kqemu'


yup,
       have downloaded gcc3.4 but when I try again I get 

> make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/i386-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/i386-user'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/arm-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/arm-user'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/armeb-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/armeb-user'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/sparc-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/sparc-user'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/ppc-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/ppc-user'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/mips-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/mips-user'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/mipsel-user'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/mipsel-user'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/i386-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/i386-softmmu'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/ppc-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/ppc-softmmu'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/sparc-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/sparc-softmmu'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/x86_64-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/x86_64-softmmu'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/mips-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/mips-softmmu'
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/arm-softmmu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/arm-softmmu'
make -C kqemu
make[1]: Entering directory `/home/jeremy/temp/qemu-0.8.0/kqemu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jeremy/temp/qemu-0.8.0/kqemu'

---

### Post by swamytk on 2006-03-08
Yes. everything is fine in your log. Compilation is successful.

---

### Post by carverj on 2006-03-08
oh, ok. so you only need to worry if theres an error message is it?
So I tried to continue with sudo make install and got the following 
FATAL error
```
make[1]: Entering directory `/home/jeremy/temp
/qemu-0.8.0/arm-softmmu'
install -m 755 -s qemu-system-arm "/usr/local/bin"
make[1]: Leaving directory `/home/jeremy/temp
/qemu-0.8.0/arm-softmmu'
cd kqemu ; ./install.sh
root@UBUNTU:/home/jeremy/temp/qemu-0.8.0# sudo 
modprobe kqemu
FATAL: Error inserting kqemu (/lib/modules/2.6.12-10-386
/misc/kqemu.ko): Invalid module format

```
:-?

Do you know what is wrong?

---

