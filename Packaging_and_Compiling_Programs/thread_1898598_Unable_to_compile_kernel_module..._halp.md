---
title: "Unable to compile kernel module... halp?"
date: 2011-12-21
forum: Packaging and Compiling Programs
---

### Post by AnrDaemon on 2011-12-21
I _know_ i'm doing something stupid... But I can't fugure out, what for exact.
Every single guide to compile kernel module go like it's self-explanatory process that does not involve any brain. Only occasionally they mention that you need kernel source or headers.
But...
```
# make config


-------------------- Ralink RT73 Station Configuration --------------------

  Linux kernel source directory [/usr/src/linux-2.6.24-30-server]: /usr/src/linux-source-2.6.24

  Linux kernel source directory : /usr/src/linux-source-2.6.24

  Module install directory : /lib/modules/2.6.24-30-server/kernel/drivers/net

# make all
make -C /lib/modules/2.6.24-30-server/build SUBDIRS=/home/anrdaemon/build/2011_0210_RT73_Linux_STA_Drv1.1.0.5/Module modules
make: *** /lib/modules/2.6.24-30-server/build: No such file or directory.  Stop.
make: *** [all] Error 2
```

Can someone walk me through the process from the very beginning, please?

P.S.
# cat /proc/version
Linux version 2.6.24-30-server (buildd@vernadsky) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Mon Nov 28 20:06:15 UTC 2011

---

### Post by SevenMachines on 2011-12-22
This,
```
 /lib/modules/2.6.24-30-server/build: No such file or directory. 
```should be the result of not having the right headers installed (they should supply the symlink 'build' directory thats missing)
```
 $ sudo apt-get install linux-headers-2.6.24-30-server
```

---

### Post by AnrDaemon on 2011-12-23
Thanks. Removing and reinstalling headers did it.
Now, to actually get this thing working... *meh*

---

