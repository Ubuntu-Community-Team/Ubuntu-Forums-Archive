---
title: "libspe2-dev, no pkg-config file.  What next?"
date: 2007-11-23
forum: Packaging and Compiling Programs
---

### Post by mickfromperth on 2007-11-23
Hi.  I'm attepmting to compile spu-medialib on a ps3 running ubunutu.

I've apt-get installed libspe2-dev to allow compilation agains libspe2.  However, spe-medialib and many other programs I've tried to compile error saying unable to locate libspe2.  I've traced this down to these programs using pkg-config as the tool to locate libspe2:

---
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBSPE2... configure: error: Package requirements (libspe2 >= 2.2.0) were not met:

No package 'libspe2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBSPE2_CFLAGS
and LIBSPE2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

mick@mick-desktop:~/build/spu-medialib$ LIBSPE2_CFLAGSLIBSPE2_CFLAGS
---

However, both libspe2 and libspe2-dev are installed:
---
mick@mick-desktop:~/build/spu-medialib$ sudo apt-get install libspe2 libspe2-dev
[sudo] password for mick:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libspe2 is already the newest version.
libspe2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mick@mick-desktop:~/build/spu-medialib$
---

This url says libspe-dev doesn't include the file libspe2.pc:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libspe2&version=gutsy&arch=powerpc](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libspe2&version=gutsy&arch=powerpc)

Hence my conclusion.

How can I resolve this?  I've attempted to create my own pkg-config file for libspe2 but this doesn't seem to fix it.  Can someone help me with some advise on what the Libs and CFlags lines should look like?

---
mick@mick-desktop:~/build/spu-medialib$ cat /usr/lib/pkgconfig/libspe2.pc
prefix=/usr
exec_prefix=/usr
libdir=/usr/lib
includedir=${prefix}/include

Name: libspe2
Description: libspe2
Version: 2.2.0
Libs: -L${libdir}
Cflags: -I${includedir}

mick@mick-desktop:~/build/spu-medialib$
---

Thanks in advance.
Mick

---

### Post by dholbach on 2007-11-23
Seems you're right. I'd file a bug report on libspe2, letting the maintainer know. [http://launchpad.net/ubuntu/+source/libspe2/+filebug](http://launchpad.net/ubuntu/+source/libspe2/+filebug)

If you want to fix this locally, I'd use the .pc file included in the source.

```
apt-get source libspe2
```

---

### Post by mickfromperth on 2007-11-23
OK thanks.  Now how do I compile and install after that?  Is there a guide somewhere??

Mick

---

### Post by mickfromperth on 2007-11-23
I fund this link:
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

Which asnwers my last question.  I've gone ahead and built libspe2 from source; and still no libspe2.pc.  Aagh.

I guess I have no choice but to do the right thing now ;-)

Mick

---

