---
title: "/usr/bin/ld: cannot find -lGL"
date: 2010-05-11
forum: Packaging and Compiling Programs
---

### Post by eXmifrator on 2010-05-11
hey guys,

When i compile a set of examples i downloaded i get this error:

/usr/bin/ld: cannot find -lGL

i think i have opengl lib installed but i cant seem to correct this error...

Any sugestions?

Thanks.

---

### Post by eXmifrator on 2010-05-12
Ok, just solved this.

The linkage was broken...

just found the library and associated the right files:

ln -s /usr/lib/libGL.so.xx.xx.xx /usr/lib/libGL.so

make sure you remove the broken libGL.so before running the command.

---

### Post by bluesquall on 2010-11-17
also in thread 409438

I had to remove the symlink (originally to mesa/libGL.so) and make a new one.

---

### Post by moijdikssekool on 2011-08-24
> hi
i have the same problem

[QUOTE]gcc main.o libk8055.o -o k8055 -lusb -L/usr/lib -lm
/usr/bin/ld: cannot find -lusb
so i check in /usr/lib, i see the lib libusb-1.0.so.0.0.0
so i tape  
> sudo ln -s /usr/lib/libusb-1.0.so.0.0.0 /usr/lib/libusb-1.0.so
the link libusb-1.0.so is created in /usr/lib (i right-click to check its properties, the target is  /usr/lib/libusb-1.0.so.0.0.0)
but the problem is still there: "/usr/bin/ld: cannot find -lusb"[/QUOTE]

false alert: i remove the number : sudo ln -s /usr/lib/libusb-1.0.so.0.0.0 /usr/lib/libusb.so
it's ok  now

---

### Post by maxxum on 2011-09-13
I'm facing a similar issue. From what I have learned, one needs to create a symbolic link. I need a little help understanding this please. WHile compiling a package I get this error
```
/usr/bin/ld cannot find -lcr
```
So I search for libcr in my root directory. There is a lot of stuff in the output. I don't see something like libcr.so though. There are a lot of libcr0 variants, however. Can someone guide me as to what to put in the link, and where to save it in a newbie friendly manner? Here is what I find in the search:
```
/usr/src/blcr-0.8.2/tests/crut_util_libcr.c
/var/lib/dkms/blcr/0.8.2/build/tests/crut_util_libcr.c
/usr/src/blcr-0.8.2/libcr
/var/lib/dkms/blcr/0.8.2/build/libcr
/usr/share/doc/libcr0
/var/cache/apt/archives/libcr0_0.8.2-15ubuntu1_amd64.deb
/var/lib/dpkg/info/libcr0.list
/var/lib/dpkg/info/libcr0.md5sums
/var/lib/dpkg/info/libcr0.postinst
/var/lib/dpkg/info/libcr0.postrm
/var/lib/dpkg/info/libcr0.shlibs
/var/lib/dpkg/info/libcr0.symbols
/usr/lib/sasl2/libcrammd5.a
/usr/lib/sasl2/libcrammd5.la
/usr/lib/sasl2/libcrammd5.so
/usr/lib/sasl2/libcrammd5.so.2
/usr/lib/sasl2/libcrammd5.so.2.0.23
/usr/src/linux-headers-2.6.38-11-generic/include/config/libcrc32c.h
/usr/src/linux-headers-2.6.38-8-generic/include/config/libcrc32c.h
/lib/modules/2.6.32-25-generic/kernel/lib/libcrc32c.ko
/lib/modules/2.6.35-28-generic/kernel/lib/libcrc32c.ko
/lib/modules/2.6.38-11-generic/kernel/lib/libcrc32c.ko
/lib/modules/2.6.38-8-generic/kernel/lib/libcrc32c.ko
/usr/src/blcr-0.8.2/include/libcr.h
/var/lib/dkms/blcr/0.8.2/build/include/libcr.h
/usr/lib32/libcroco-0.6.so
/usr/lib/libcroco-0.6.so.3
/usr/lib32/libcroco-0.6.so.3
/usr/lib/libcroco-0.6.so.3.0.1
/usr/lib32/libcroco-0.6.so.3.0.1
/usr/share/doc/libcroco3
/var/lib/dpkg/info/libcroco3.list
/var/lib/dpkg/info/libcroco3.md5sums
/var/lib/dpkg/info/libcroco3.postinst
/var/lib/dpkg/info/libcroco3.postrm
/var/lib/dpkg/info/libcroco3.shlibs
/usr/lib/libcr_omit.so.0
/usr/lib/libcr_omit.so.0.5.2
/usr/lib/vlc/plugins/video_filter/libcroppadd_plugin.so
/usr/lib/vlc/plugins/video_filter/libcrop_plugin.so
/usr/lib/libcr_run.so.0
/usr/lib/libcr_run.so.0.5.2
/usr/lib/libcr.so.0
/usr/lib/libcr.so.0.5.2
/usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
/usr/lib32/gtk-2.0/2.10.0/engines/libcrux-engine.so
/lib/x86_64-linux-gnu/libcrypt-2.13.so
/lib32/libcrypt-2.13.so
/usr/lib/x86_64-linux-gnu/libcrypt.a
/lib32/libcrypto.so
/lib/libcrypto.so.0.9.8
/lib32/libcrypto.so.0.9.8
/usr/lib/libcrypto.so.0.9.8
/usr/lib32/libcrypto.so.0.9.8
/usr/share/doc/libcrypt-passwdmd5-perl
/var/lib/dpkg/info/libcrypt-passwdmd5-perl.list
/var/lib/dpkg/info/libcrypt-passwdmd5-perl.md5sums
/usr/lib/x86_64-linux-gnu/libcrypt.so
/lib/x86_64-linux-gnu/libcrypt.so.1
/lib32/libcrypt.so.1
/usr/share/doc/libcryptui0
/var/lib/dpkg/info/libcryptui0.list
/var/lib/dpkg/info/libcryptui0.md5sums
/var/lib/dpkg/info/libcryptui0.postinst
/var/lib/dpkg/info/libcryptui0.postrm
/var/lib/dpkg/info/libcryptui0.shlibs
/usr/lib/libcryptui.so.0
/usr/lib/libcryptui.so.0.0.0
```

---

### Post by SevenMachines on 2011-09-13
Manual linking is not usually required, usually its a sign of something broken if nothing else. In general,

* ```
/usr/bin/ld cannot find -lcr
```Ok, so it cant find libcr.so, these /usr/lib/libsomelib.so are usually symlinks to actual libraries set up by -dev packages specifically for developers

* Lets use apt-file to find what package we need
```
$ sudo apt-file update
$ apt-file search libcr.so
lib32cr0: /usr/lib32/libcr.so.0
lib32cr0: /usr/lib32/libcr.so.0.5.2
libcr-dbg: /usr/lib/debug/usr/lib/libcr.so.0.5.2
libcr-dbg: /usr/lib/debug/usr/lib32/libcr.so.0.5.2
libcr-dev: /usr/lib/libcr.so
libcr0: /usr/lib/libcr.so.0
libcr0: /usr/lib/libcr.so.0.5.2
```* So the libcr-dev package is the one we want
```
$ sudo apt-get install libcr-dev
$ ls -l /usr/lib/libcr.so
lrwxrwxrwx 1 root root 14 Dec 15  2010 /usr/lib/libcr.so -> libcr.so.0.5.2
```Usually that sort of method will find what package you want

---

### Post by SevenMachines on 2011-09-13
p.s Its best to open a new thread rather than re-awaken an old similar one

---

### Post by maxxum on 2011-09-13
Great. That helped. Thanks!!

---

