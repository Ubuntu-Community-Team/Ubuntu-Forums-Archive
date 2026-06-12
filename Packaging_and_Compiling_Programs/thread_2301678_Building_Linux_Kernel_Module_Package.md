---
title: "Building Linux Kernel Module Package"
date: 2015-11-04
forum: Packaging and Compiling Programs
---

### Post by actionmystique on 2015-11-04
Hello everyone,

[FONT=arial]I'm trying to build a debian package for all new **Realtek WiFi drivers** based on [**Linux kernel 4.3.0**]("https://github.com/torvalds/linux") and release it to the public so they can install them on Ubuntu 15.10 (linux 4.2.0-16). The latest [**backported drivers**]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/") are already old (4.2.0).[/FONT]

[FONT=arial]So far, I've been able to install the kernel module from the Linus Torvald github sources with:[/FONT]
[FONT=arial]
[LIST]
[*]make oldconfig
[*]make prepare
[*]make modules_prepare
[*]make modules SUBDIRS=scripts
[*]make modules SUBDIRS=scripts/mod
[*]make modules SUBDIRS=drivers/net/wireless/rtlwifi
[*]make modules_install SUBDIRS=drivers/net/wireless/rtlwifi
[/LIST]
This installs the drivers inside [B]/lib/modules/4.3.0+
[/B][/FONT]ls -al
total 12
drwxr-xr-x  3 root root 4096 Nov  4 15:28 .
drwxr-xr-x  9 root root 4096 Nov  4 15:39 ..
drwxr-xr-x 14 root root 4096 Nov  4 15:28 extra[FONT=arial]:[/FONT]

[FONT=arial]ls -al extra
total 5012
drwxr-xr-x 14 root root    4096 Nov  4 15:28 .
drwxr-xr-x  3 root root    4096 Nov  4 15:28 ..
drwxr-xr-x  2 root root    4096 Nov  4 15:28 btcoexist
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8188ee
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8192c
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8192ce
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8192cu
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8192de
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8192ee
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8192se
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8723ae
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8723be
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8723com
drwxr-xr-x  2 root root    4096 Nov  4 15:28 rtl8821ae
-rw-r--r--  1 root root  640256 Nov  4 15:28 rtl_pci.ko
-rw-r--r--  1 root root  533960 Nov  4 15:28 rtl_usb.ko
-rw-r--r--  1 root root 3892776 Nov  4 15:28 rtlwifi.ko
[/FONT]
[FONT=arial]The directory tree is different on current **/lib/modules**[/FONT]**/4.2.0-16-generic**:[FONT=arial]
[/FONT]ls -al
total 4384
drwxr-xr-x  6 root root    4096 Nov  2 10:42 .
drwxr-xr-x  9 root root    4096 Nov  4 15:39 ..
lrwxrwxrwx  1 root root      39 Oct  8 19:26 build -> /usr/src/linux-headers-4.2.0-16-generic
drwxr-xr-x  2 root root    4096 Oct  8 19:17 initrd
drwxr-xr-x 12 root root    4096 Oct 24 21:16 kernel
-rw-r--r--  1 root root 1021056 Nov  2 10:42 modules.alias
-rw-r--r--  1 root root 1010099 Nov  2 10:42 modules.alias.bin
-rw-r--r--  1 root root    6578 Oct  8 19:15 modules.builtin
-rw-r--r--  1 root root    8453 Nov  2 10:42 modules.builtin.bin
-rw-r--r--  1 root root  458321 Nov  2 10:42 modules.dep
-rw-r--r--  1 root root  656631 Nov  2 10:42 modules.dep.bin
-rw-r--r--  1 root root     263 Nov  2 10:42 modules.devname
-rw-r--r--  1 root root  176160 Oct  8 19:15 modules.order
-rw-r--r--  1 root root      84 Nov  2 10:42 modules.softdep
-rw-r--r--  1 root root  494409 Nov  2 10:42 modules.symbols
-rw-r--r--  1 root root  604365 Nov  2 10:42 modules.symbols.bin
drwxr-xr-x  6 root root    4096 Nov  2 10:41 updates
drwxr-xr-x  3 root root    4096 Oct 24 21:04 vdso

[FONT=arial]I'm stuck here. I don't know how to build the package with checkinstall so that the drivers are used with the current linux kernel.[/FONT]
[FONT=arial]Also, it seems that some files are missing in my build folder & I don't know how to generate them:[/FONT]
[FONT=arial]
[LIST]
[*]modules.order
[*]Module.symvers
[*]...
[/LIST]
Your assistance would be greatly appreciated.

P.S: all the Ubuntu packages that I have built & released so far are available [here]("https://github.com/jean-christophe-manciot").[/FONT]

---

