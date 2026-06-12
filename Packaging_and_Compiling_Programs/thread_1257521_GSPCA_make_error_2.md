---
title: "GSPCA make error 2"
date: 2009-09-03
forum: Packaging and Compiling Programs
---

### Post by jesterthejedi on 2009-09-03
Trying to build the gspca from a source deb. Error 2 happens whether I do from make, sudo make install or sudo m-a prepare and then sudo m-a a-i gspca. Here is the latter output log:

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
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-9-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.31-9-generic/g ;s/#KVERS#/2.6.31-9-generic/g ; s/_KVERS_/2.6.31-9-generic/g ; s/##KDREV##/2.6.31-9.29/g ; s/#KDREV#/2.6.31-9.29/g ; s/_KDREV_/2.6.31-9.29/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.31-9-generic KERNELDIR=/usr/src/linux-headers-2.6.31-9-generic
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux-headers-2.6.31-9-generic SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-9-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/usr/src/modules/gspca/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-9-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2

---

### Post by jesterthejedi on 2009-09-06
Bump
anyone know why this error is coming up?

---

### Post by jesterthejedi on 2009-09-13
solved by using:

make distclean
make clean
make menuconfig, and only installing what i needed

ran a normal install with:
sudo make install

now working on karmic!

---

### Post by y-u-h on 2009-11-01
a little question from noob :o
1. 'make clean' works but 'make distclean' and 'make menuconfig' doesn't work:
step0@bubu-ntu:~/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/gspcav1-20071224$ make distclean
make: *** &#1053;&#1077;&#1090; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1072; &#1076;&#1083;&#1103; &#1089;&#1073;&#1086;&#1088;&#1082;&#1080; &#1094;&#1077;&#1083;&#1080; `distclean'.  &#1054;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;.
what can I do with my karmic?

---

### Post by hannibal_lecter on 2009-11-12
Can you explain more about your procedure? thanks

---

### Post by jesterthejedi on 2009-11-15
Try sudo for each of those and see if you still have errors. With the menuconfig I can edit what drivers to load with the install, that removed errors on compiling the source.

---

