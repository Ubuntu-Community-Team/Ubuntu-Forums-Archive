---
title: "MOdule Assistant and Webcam Problems"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by BGFG on 2008-06-26
Hi,
(posted this over in Multimedia and Video but no response)
I have a MSI starcam 370i and I'v been trying to install both the gspca and ov511 drivers using module assistant but i've been unsuccessful so far. Please take a look at my log file output and tell me what may be wrong. Thanks for any help.

GSPCA:

```
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[1]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[1]: Leaving directory `/usr/src/modules/gspca'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/gspca'
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[2]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[2]: Leaving directory `/usr/src/modules/gspca'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.24-19-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.24-19-generic/g ;s/#KVERS#/2.6.24-19-generic/g ; s/_KVERS_/2.6.24-19-generic/g ; s/##KDREV##/2.6.24-19.34/g ; s/#KDREV#/2.6.24-19.34/g ; s/_KDREV_/2.6.24-19.34/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.24-19-generic KERNELDIR=/usr/src/linux-headers-2.6.24-19-generic
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/modules/gspca/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2
```


ov511:
```


for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.24-19-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.24-19-generic/g ;s/#KVERS#/2.6.24-19-generic/g ; s/_KVERS_/2.6.24-19-generic/g ; s/##KDREV##/2.6.24-19.34/g ; s/#KDREV#/2.6.24-19.34/g ; s/_KDREV_/2.6.24-19.34/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_clean
/usr/bin/make KDIR=/usr/src/linux INCLUDEDIR=/usr/src/linux/include KVERS=2.6.24-19-generic clean
make[1]: Entering directory `/usr/src/modules/ov511'
/usr/bin/make -C /usr/src/linux M=/usr/src/modules/ov511 clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: Leaving directory `/usr/src/modules/ov511'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ov511'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.24-19-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.24-19-generic/g ;s/#KVERS#/2.6.24-19-generic/g ; s/_KVERS_/2.6.24-19-generic/g ; s/##KDREV##/2.6.24-19.34/g ; s/#KDREV#/2.6.24-19.34/g ; s/_KDREV_/2.6.24-19.34/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_clean
/usr/bin/make KDIR=/usr/src/linux INCLUDEDIR=/usr/src/linux/include KVERS=2.6.24-19-generic clean
make[2]: Entering directory `/usr/src/modules/ov511'
/usr/bin/make -C /usr/src/linux M=/usr/src/modules/ov511 clean
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: Leaving directory `/usr/src/modules/ov511'
make[1]: Nothing to be done for `kdist_config'.
dh_testdir
dh_testroot
dh_clean -k
/usr/bin/make KDIR=/usr/src/linux INCLUDEDIR=/usr/src/linux/include KVERS=2.6.24-19-generic
make[2]: Entering directory `/usr/src/modules/ov511'
    Building OVCam drivers for 2.6 kernel.
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/ov511 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/src/modules/ov511/ov511_core.o
/usr/src/modules/ov511/ov511_core.c:29:26: error: linux/config.h: No such file or directory
/usr/src/modules/ov511/ov511_core.c:1701: error: unknown field ‘algo_control’ specified in initializer
/usr/src/modules/ov511/ov511_core.c:1701: warning: initialization from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:1711: error: unknown field ‘algo_control’ specified in initializer
/usr/src/modules/ov511/ov511_core.c:1711: warning: initialization from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c: In function ‘ov51x_init_isoc’:
/usr/src/modules/ov511/ov511_core.c:3566: warning: assignment from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c: At top level:
/usr/src/modules/ov511/ov511_core.c:4983: error: unknown field ‘hardware’ specified in initializer
/usr/src/modules/ov511/ov511_core.c:4983: error: ‘VID_HARDWARE_OV511’ undeclared here (not in a function)
/usr/src/modules/ov511/ov511_core.c: In function ‘cd_to_ov’:
/usr/src/modules/ov511/ov511_core.c:5543: warning: initialization from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c: In function ‘ov_create_sysfs’:
/usr/src/modules/ov511/ov511_core.c:5637: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5638: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5639: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5640: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5641: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5642: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5643: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5644: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/ov511/ov511_core.c:5645: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
make[4]: *** [/usr/src/modules/ov511/ov511_core.o] Error 1
make[3]: *** [_module_/usr/src/modules/ov511] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/ov511'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ov511'
make: *** [kdist_build] Error 2
```

---

### Post by cariboo on 2008-06-26
Both gspca and and ov511 are included in the kernel you don't have to compile them yourself. To load the modules in a terminal type:

```
sudo modprobe gspca
```

and

```
sudo modprobe ov511
```

You won't see anything echoed back. To see if they loaded in a terminal type:

```
lsmod
```

Jim

---

### Post by BGFG on 2008-06-27
Hi Jim,
As you said, they loaded. Thanks a lot. I will let you know how things go with the webcam.

---

### Post by BGFG on 2008-06-27
Works like a gem, colours a little off. but i'll find something in the repositories to tweak that.

Thanks!

---

