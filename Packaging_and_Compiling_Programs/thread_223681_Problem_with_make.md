---
title: "Problem with make"
date: 2006-07-26
forum: Packaging and Compiling Programs
---

### Post by sidlinux on 2006-07-26
I tried running the make command (with the sudo) and I get an error that says that /lib/linux/2.6.15-26/build (or whatever path it is if I'm wrong)  I'm trying to install an updated zd1211 driver (not the one that came with ubuntu), which is from the source when the error showed up.  I also tried to install ndiswrapper version 1.21 (the one I downloaded from sourceforge) and still produced the same error.  Anyways, it said something about the /lib/linux-2.6.15-26/build file or folder missing.  Any ideas what I should do?  Thanks in advance.

Sidney

---

### Post by mlind on 2006-07-26
install kernel-headers package
```

sudo aptitude install kernel-headers-$(uname -r)

```

And make sure you have build-essential package installed too.

---

### Post by sidlinux on 2006-08-05
I installed the following packages:

[LIST]
[*]kernel-headers
[*]build-essential
[/LIST]

Still have no luck in resolving the error.  Here's what I have to be more specific:

sidney@katherine-dell:~/Drivers$ ls
broadcom  zd1211-driver-r77
sidney@katherine-dell:~/Drivers$ cd zd1211-driver-r77/
sidney@katherine-dell:~/Drivers/zd1211-driver-r77$ ls
apdbg.c  copying  Makefile  src  sta

**Here's where it all starts:**

sidney@katherine-dell:~/Drivers/zd1211-driver-r77$ make
/lib/modules/2.6.15-26-686/build
/home/sidney/Drivers/zd1211-driver-r77
-I/home/sidney/Drivers/zd1211-driver-r77/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211B
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/sidney/Drivers/zd1211-driver-r77 modules
make: *** /lib/modules/2.6.15-26-686/build: No such file or directory.  Stop.
make: *** [all] Error 2
sidney@katherine-dell:~/Drivers/zd1211-driver-r77$


Any help is appreciated.

Sidney

---

### Post by mlind on 2006-08-05
I'm sorry, I should have instructed you to install **linux-headers**-$(uname -r) instead. You can remove the kernel-headers package.

---

