---
title: "ibcs 3.4 on ubuntu server"
date: 2007-11-27
forum: Packaging and Compiling Programs
---

### Post by msteidley on 2007-11-27
I'm trying to compile ibcs 3.4 from the Linux ABI project on a server install with the 2.6.22-14-server kernel. It insisted on using '/lib/modules/2.6.22-14-server/build' so I linked it to '/usr/src/linux-headers-2.6.22-14-server'.

Below is the output when I run make.

```
root@gutsy:~/ibcs-3_4# make
make -C /lib/modules/2.6.22-14-server/build M=/root/ibcs-3_4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-server'
  CC [M]  /root/ibcs-3_4/coff/binfmt-coff.o
  LD [M]  /root/ibcs-3_4/coff/binfmt_coff.o
  CC [M]  /root/ibcs-3_4/cxenix/sysent.o
  CC [M]  /root/ibcs-3_4/cxenix/misc.o
  CC [M]  /root/ibcs-3_4/cxenix/stubs.o
  CC [M]  /root/ibcs-3_4/cxenix/signal.o
  CC [M]  /root/ibcs-3_4/cxenix/pathconf.o
  CC [M]  /root/ibcs-3_4/cxenix/utsname.o
  LD [M]  /root/ibcs-3_4/cxenix/abi_cxenix.o
  CC [M]  /root/ibcs-3_4/ibcs/sysent.o
  LD [M]  /root/ibcs-3_4/ibcs/abi_ibcs.o
  CC [M]  /root/ibcs-3_4/isc/sysent.o
  LD [M]  /root/ibcs-3_4/isc/abi_isc.o
  CC [M]  /root/ibcs-3_4/lcall/lcall.o
  AS [M]  /root/ibcs-3_4/lcall/entry.o
  LD [M]  /root/ibcs-3_4/lcall/abi_lcall.o
  CC [M]  /root/ibcs-3_4/sco/sysent.o
  CC [M]  /root/ibcs-3_4/sco/misc.o
  CC [M]  /root/ibcs-3_4/sco/mmap.o
  CC [M]  /root/ibcs-3_4/sco/ptrace.o
  CC [M]  /root/ibcs-3_4/sco/secureware.o
  CC [M]  /root/ibcs-3_4/sco/stat.o
  CC [M]  /root/ibcs-3_4/sco/statvfs.o
  CC [M]  /root/ibcs-3_4/sco/ioctl.o
  CC [M]  /root/ibcs-3_4/sco/termios.o
  CC [M]  /root/ibcs-3_4/sco/tapeio.o
  CC [M]  /root/ibcs-3_4/sco/vtkbd.o
  LD [M]  /root/ibcs-3_4/sco/abi_sco.o
  CC [M]  /root/ibcs-3_4/solaris/lfs.o
  CC [M]  /root/ibcs-3_4/solaris/solarisx86.o
  CC [M]  /root/ibcs-3_4/solaris/socket.o
  CC [M]  /root/ibcs-3_4/solaris/stat.o
  CC [M]  /root/ibcs-3_4/solaris/sysent.o
  LD [M]  /root/ibcs-3_4/solaris/abi_solaris.o
  CC [M]  /root/ibcs-3_4/svr4/hrtsys.o
  CC [M]  /root/ibcs-3_4/svr4/ioctl.o
  CC [M]  /root/ibcs-3_4/svr4/ipc.o
  CC [M]  /root/ibcs-3_4/svr4/mmap.o
  CC [M]  /root/ibcs-3_4/svr4/open.o
  CC [M]  /root/ibcs-3_4/svr4/svr4.o
  CC [M]  /root/ibcs-3_4/svr4/sysconf.o
  CC [M]  /root/ibcs-3_4/svr4/sysfs.o
  CC [M]  /root/ibcs-3_4/svr4/sysinfo.o
  CC [M]  /root/ibcs-3_4/svr4/sysi86.o
  CC [M]  /root/ibcs-3_4/svr4/ulimit.o
  CC [M]  /root/ibcs-3_4/svr4/utsname.o
  CC [M]  /root/ibcs-3_4/svr4/stream.o
  CC [M]  /root/ibcs-3_4/svr4/stat.o
  CC [M]  /root/ibcs-3_4/svr4/socksys.o
In file included from /root/ibcs-3_4/svr4/socksys.c:51:
/root/ibcs-3_4/svr4/../include/util/revalidate.h: In function ‘do_revalidate’:
/root/ibcs-3_4/svr4/../include/util/revalidate.h:32: warning: passing argument 2 of ‘notify_change’ from incompatible pointer type
/root/ibcs-3_4/svr4/../include/util/revalidate.h:32: error: too few arguments to function ‘notify_change’
make[3]: *** [/root/ibcs-3_4/svr4/socksys.o] Error 1
make[2]: *** [/root/ibcs-3_4/svr4] Error 2
make[1]: *** [_module_/root/ibcs-3_4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-server'
make: *** [all] Error 2

```

Any help would be appreciated.

---

### Post by Firedorn on 2007-11-29
I'm working on the same thing here, I'll post any finds.  I have yet to begin, so I figured I'd look here to start off.

---

### Post by Firedorn on 2007-11-30
Well, it seems like it is strongly suggested to run the patch on a vanilla kernel, so I tried a couple, especially 2.6.22.3, using the patch in the project page (on sourceforge).  Well the kernel compiled properly, booted ok but I can't get the binaries to run.  So I'm not that far ahead.

Any help is appreciated.  I'll poste specifics soon.

---

### Post by msteidley on 2007-12-28
I edited include/util/revalidate.h to add the NULL value between the dentry and &attr:

```
#if _KSL > 21 && defined(CONFIG_SUSE_KERNEL)
        error = notify_change(dentry,NULL,&attr);
#else
        error = notify_change(dentry,NULL,&attr);
#endif
```

and after that it compiled and the abi_ldr script was able to load all the modules. I'm still testing with my legacy applications.

---

