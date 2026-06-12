---
title: "$DESTDIR's not there....bit of a problem."
date: 2011-11-14
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-11-14
Hi guys! Probably a noob question, but still...

Attempting to package a program, more to prove it to myself than to release it, anyways, $(DESTDIR) in the makefile is blank. No, I haven't been messing around with anything, exporting DESTDIR or anything. So it tries to install as make usually would when I run make, i.e. to the root of filesystem, not $(DESTDIR)/usr/bin or whatever.

I put 'env' in the makefile, here's the output of it:

```
env
DEB_BUILD_ARCH_OS=linux
DH_INTERNAL_BUILDFLAGS=1
CPPFLAGS=
CFLAGS=-g -O2
DEB_HOST_ARCH_BITS=32
CXXFLAGS=-g -O2
DEB_BUILD_GNU_CPU=i686
PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11
GPG_AGENT_INFO=/tmp/keyring-Bih1YK/gpg:0:1
DEB_HOST_ARCH_CPU=i386
FFLAGS=-g -O2
DEB_HOST_ARCH_ENDIAN=little
DEB_HOST_GNU_SYSTEM=linux-gnu
LDFLAGS=-Wl,-Bsymbolic-functions
DEB_BUILD_ARCH=i386
HOME=/home/michael
LOGNAME=michael
DEB_HOST_GNU_TYPE=i686-linux-gnu
DEB_HOST_ARCH_OS=linux
DEB_BUILD_ARCH_BITS=32
MAKEFLAGS=w
DEB_BUILD_GNU_TYPE=i686-linux-gnu
MFLAGS=-w
DEB_BUILD_ARCH_CPU=i386
DEB_BUILD_ARCH_ENDIAN=little
DEB_HOST_GNU_CPU=i686
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_HOST_MULTIARCH=i386-linux-gnu
DEB_HOST_ARCH=i386
DEB_BUILD_MULTIARCH=i386-linux-gnu
LANG=en_GB.UTF-8
TERM=xterm
MAKELEVEL=2

```

Anyone got any ideas? :(

Of course I could export destdir, but that kinda defeats the point of it.

---

### Post by Bachstelze on 2011-11-15
How exactly are you calling make ?

```
firas@av104151 ~ % cat Makefile  
all:
	env
firas@av104151 ~ % DESTDIR=/foo make | grep DESTDIR
DESTDIR=/foo

```

---

### Post by MG&amp;TL on 2011-11-15
I'm not, I'm letting whatever part of debhelper call it for me, as per usual.

---

### Post by MG&amp;TL on 2011-11-15
I'll try setting DESTDIR, as in your code.

---

### Post by Bachstelze on 2011-11-15
Can you post your debian/rules then?

---

### Post by MG&amp;TL on 2011-11-15
Just as per-usual from dh_make. Sorry, not at the right computer. The default dh_make file, something like:

```


##headery stuff

     dh@
```

---

### Post by Bachstelze on 2011-11-15
Well then I don't know why you're not seeing DESTDIR in make's env, because I do have it here (line 77):

```

     4	 dpkg-buildpackage -rfakeroot -D -us -uc
     5	dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
     6	dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
     7	dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
     8	dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
     9	dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
    10	dpkg-buildpackage: source package helloworld
    11	dpkg-buildpackage: source version 1.0-1
    12	dpkg-buildpackage: source changed by Firas Kraiem <firas@fkraiem.org>
    13	 dpkg-source --before-build helloworld-1.0
    14	dpkg-buildpackage: host architecture i386
    15	 fakeroot debian/rules clean
    16	dh clean 
    17	   dh_testdir
    18	   dh_auto_clean
    19	make[1]: Entering directory `/home/firas/software/ubuntu/packages/helloworld-1.0'
    20	rm -f hello.o hello
    21	make[1]: Leaving directory `/home/firas/software/ubuntu/packages/helloworld-1.0'
    22	   dh_clean
    23	 dpkg-source -b helloworld-1.0
    24	dpkg-source: info: using source format `3.0 (quilt)'
    25	dpkg-source: info: building helloworld using existing ./helloworld_1.0.orig.tar.gz
    26	dpkg-source: warning: newly created empty file 'debuilt.txt' will not be represented in diff
    27	dpkg-source: info: local changes stored in helloworld-1.0/debian/patches/debian-changes-1.0-1, the modified files are:
    28	 helloworld-1.0/Makefile
    29	dpkg-source: info: building helloworld in helloworld_1.0-1.debian.tar.gz
    30	dpkg-source: info: building helloworld in helloworld_1.0-1.dsc
    31	 debian/rules build
    32	dh build 
    33	   dh_testdir
    34	   dh_auto_configure
    35	   dh_auto_build
    36	make[1]: Entering directory `/home/firas/software/ubuntu/packages/helloworld-1.0'
    37	gcc -std=c99 -pedantic -Wall -Wextra -Werror   -c -o hello.o hello.c
    38	gcc -o hello hello.o
    39	make[1]: Leaving directory `/home/firas/software/ubuntu/packages/helloworld-1.0'
    40	   dh_auto_test
    41	 fakeroot debian/rules binary
    42	dh binary 
    43	   dh_testroot
    44	   dh_prep
    45	   dh_installdirs
    46	   dh_auto_install
    47	make[1]: Entering directory `/home/firas/software/ubuntu/packages/helloworld-1.0'
    48	env
    49	DEB_BUILD_ARCH_OS=linux
    50	DH_INTERNAL_BUILDFLAGS=1
    51	CPPFLAGS=
    52	_=debian/rules
    53	CFLAGS=-std=c99 -pedantic -Wall -Wextra -Werror
    54	DEB_HOST_ARCH_BITS=32
    55	CXXFLAGS=-g -O2
    56	DEBEMAIL=firas@fkraiem.org
    57	DEB_BUILD_ARCH_BITS=32
    58	DEB_BUILD_GNU_CPU=i686
    59	PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11
    60	DEB_BUILD_MULTIARCH=i386-linux-gnu
    61	GPG_AGENT_INFO=/tmp/gpg-c4OsMW/S.gpg-agent:1215:1
    62	DEB_HOST_ARCH_CPU=i386
    63	FFLAGS=-g -O2
    64	DEB_HOST_ARCH_ENDIAN=little
    65	DEB_HOST_GNU_SYSTEM=linux-gnu
    66	LDFLAGS=-Wl,-Bsymbolic-functions
    67	LD_PRELOAD=libfakeroot-sysv.so
    68	DEB_BUILD_ARCH=i386
    69	PWD=/home/firas/software/ubuntu/packages/helloworld-1.0
    70	HOME=/home/firas
    71	LD_LIBRARY_PATH=/usr/lib/libfakeroot:/usr/lib64/libfakeroot:/usr/lib32/libfakeroot
    72	LOGNAME=firas
    73	DEB_HOST_GNU_TYPE=i686-linux-gnu
    74	SHLVL=1
    75	DEB_HOST_ARCH_OS=linux
    76	MAKEOVERRIDES=${-*-command-variables-*-}
    77	DESTDIR=/home/firas/software/ubuntu/packages/helloworld-1.0/debian/helloworld
    78	MAKEFLAGS=w -- DESTDIR=/home/firas/software/ubuntu/packages/helloworld-1.0/debian/helloworld
    79	MFLAGS=-w
    80	DEB_BUILD_ARCH_CPU=i386
    81	DEB_BUILD_ARCH_ENDIAN=little
    82	DEB_HOST_GNU_CPU=i686
    83	DEB_BUILD_GNU_SYSTEM=linux-gnu
    84	LC_ALL=en_GB.UTF-8
    85	DEB_HOST_MULTIARCH=i386-linux-gnu
    86	FAKEROOTKEY=745530700
    87	GPG_TTY=/dev/pts/7
    88	DEB_HOST_ARCH=i386
    89	DEB_BUILD_GNU_TYPE=i686-linux-gnu
    90	LANG=en_GB.UTF-8
    91	TERM=screen
    92	FAKED_MODE=unknown-is-root
    93	MAKELEVEL=2
    94	install -d -o root /home/firas/software/ubuntu/packages/helloworld-1.0/debian/helloworld/usr/bin
    95	install -o root hello /home/firas/software/ubuntu/packages/helloworld-1.0/debian/helloworld/usr/bin
    96	make[1]: Leaving directory `/home/firas/software/ubuntu/packages/helloworld-1.0'
    97	   dh_install
    98	   dh_installdocs
    99	   dh_installchangelogs
   100	   dh_installexamples
   101	   dh_installman
   102	   dh_installcatalogs
   103	   dh_installcron
   104	   dh_installdebconf
   105	   dh_installemacsen
   106	   dh_installifupdown
   107	   dh_installinfo
   108	   dh_pysupport
   109	   dh_installinit
   110	   dh_installmenu
   111	   dh_installmime
   112	   dh_installmodules
   113	   dh_installlogcheck
   114	   dh_installlogrotate
   115	   dh_installpam
   116	   dh_installppp
   117	   dh_installudev
   118	   dh_installwm
   119	   dh_installxfonts
   120	   dh_installgsettings
   121	   dh_bugfiles
   122	   dh_ucf
   123	   dh_lintian
   124	   dh_gconf
   125	   dh_icons
   126	   dh_perl
   127	   dh_usrlocal
   128	   dh_link
   129	   dh_compress
   130	   dh_fixperms
   131	   dh_strip
   132	   dh_makeshlibs
   133	   dh_shlibdeps
   134	   dh_installdeb
   135	   dh_gencontrol
   136	   dh_md5sums
   137	   dh_builddeb
   138	dpkg-deb: building package `helloworld' in `../helloworld_1.0-1_i386.deb'.
   139	 dpkg-genchanges  >../helloworld_1.0-1_i386.changes
   140	dpkg-genchanges: including full source code in upload
   141	 dpkg-source --after-build helloworld-1.0
   142	dpkg-buildpackage: full upload (original source is included)
   143	Now running lintian...
   144	W: helloworld source: format-3.0-but-debian-changes-patch
   145	W: helloworld: new-package-should-close-itp-bug
   146	W: helloworld: wrong-bug-number-in-closes l3:#nnnn
   147	E: helloworld: helper-templates-in-copyright
   148	W: helloworld: copyright-has-url-from-dh_make-boilerplate
   149	E: helloworld: copyright-contains-dh_make-todo-boilerplate
   150	W: helloworld: readme-debian-contains-debmake-template
   151	W: helloworld: description-synopsis-starts-with-article
   152	W: helloworld: binary-without-manpage usr/bin/hello
   153	Finished running lintian.
   154	Now signing changes and any dsc files...
   155	 signfile helloworld_1.0-1.dsc Firas Kraiem <firas@fkraiem.org>
   156	
   157	You need a passphrase to unlock the secret key for
   158	user: "Firas Kraiem <firas@fkraiem.org>"
   159	1024-bit DSA key, ID 8E4A2650, created 2007-12-05
   160	
   161	
   162	 signfile helloworld_1.0-1_i386.changes Firas Kraiem <firas@fkraiem.org>
   163	
   164	You need a passphrase to unlock the secret key for
   165	user: "Firas Kraiem <firas@fkraiem.org>"
   166	1024-bit DSA key, ID 8E4A2650, created 2007-12-05
   167	
   168	
   169	Successfully signed dsc and changes files

```

---

### Post by MG&amp;TL on 2011-11-15
Hmmm...I did create the Makefile AFTER I did dh_make-would that affect it?

I know I'm not supposed to, but the package came as raw source with no autoconf or anything. I'll try again in morning with new Makefile.

---

### Post by Bachstelze on 2011-11-15
> **MG&TL said:**
> Hmmm...I did create the Makefile AFTER I did dh_make-would that affect it?


Not that I know of. What does your Makefile look like (especially, where do you put the env command)?

---

### Post by MG&amp;TL on 2011-11-15
first I had all of the install stuff, but no I've just edited it down to:

```
all:

      env
```

---

### Post by Bachstelze on 2011-11-15
Well, DESTDIR only makes sense in the install rule, so debhelper probably does not pass it when it calls other rules.

---

### Post by MG&amp;TL on 2011-11-16
gotcha. :D Works now. Thanks, bachstelze!

---

