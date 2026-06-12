---
title: "QEMU 7.0 Compiling Error &amp; Problem"
date: 2005-05-11
forum: Packaging and Compiling Programs
---

### Post by AgenT on 2005-05-11
I am trying to compile qemu-0.7.0 without kqemu so that it is easier to fix my problem. 

When compiling I get this error:

 ```
$ make
gcc -Wall -O2 -g -fno-strict-aliasing  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o dyngen dyngen.c
gcc -DQEMU_TOOL -Wall -O2 -g -fno-strict-aliasing -g -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o qemu-img qemu-img.c block.c block-cow.c block-qcow.c aes.c block-vmdk.c block-cloop.c block-dmg.c block-bochs.c block-vpc.c -lz
block-qcow.c:26:18: zlib.h: No such file or directory
block-qcow.c: In function `decompress_buffer':
block-qcow.c:407: error: `z_stream' undeclared (first use in this function)
block-qcow.c:407: error: (Each undeclared identifier is reported only once
block-qcow.c:407: error: for each function it appears in.)
block-qcow.c:407: error: syntax error before "strm1"
block-qcow.c:410: error: `strm' undeclared (first use in this function)
block-qcow.c:417: warning: implicit declaration of function `inflateInit2'
block-qcow.c:418: error: `Z_OK' undeclared (first use in this function)
block-qcow.c:420: warning: implicit declaration of function `inflate'
block-qcow.c:420: error: `Z_FINISH' undeclared (first use in this function)
block-qcow.c:422: error: `Z_STREAM_END' undeclared (first use in this function)
block-qcow.c:422: error: `Z_BUF_ERROR' undeclared (first use in this function)
block-qcow.c:424: warning: implicit declaration of function `inflateEnd'
block-qcow.c: In function `qcow_compress_cluster':
block-qcow.c:609: error: `z_stream' undeclared (first use in this function)
block-qcow.c:609: error: syntax error before "strm"
block-qcow.c:622: error: `strm' undeclared (first use in this function)
block-qcow.c:623: warning: implicit declaration of function `deflateInit2'
block-qcow.c:623: error: `Z_DEFAULT_COMPRESSION' undeclared (first use in this function)
block-qcow.c:624: error: `Z_DEFLATED' undeclared (first use in this function)
block-qcow.c:625: error: `Z_DEFAULT_STRATEGY' undeclared (first use in this function)
block-qcow.c:636: warning: implicit declaration of function `deflate'
block-qcow.c:636: error: `Z_FINISH' undeclared (first use in this function)
block-qcow.c:637: error: `Z_STREAM_END' undeclared (first use in this function)
block-qcow.c:637: error: `Z_OK' undeclared (first use in this function)
block-qcow.c:639: warning: implicit declaration of function `deflateEnd'
block-cloop.c:26:18: zlib.h: No such file or directory
block-cloop.c:37: error: syntax error before "z_stream"
block-cloop.c:37: warning: no semicolon at end of struct or union
block-cloop.c:38: warning: type defaults to `int' in declaration of `BDRVCloopState'
block-cloop.c:38: warning: data definition has no type or storage class
block-cloop.c: In function `cloop_open':
block-cloop.c:55: error: `s' undeclared (first use in this function)
block-cloop.c:55: error: (Each undeclared identifier is reported only once
block-cloop.c:55: error: for each function it appears in.)
block-cloop.c:96: warning: implicit declaration of function `inflateInit'
block-cloop.c:96: error: `Z_OK' undeclared (first use in this function)
block-cloop.c: At top level:
block-cloop.c:105: error: syntax error before '*' token
block-cloop.c: In function `cloop_read_block':
block-cloop.c:107: error: `s' undeclared (first use in this function)
block-cloop.c:107: error: `block_num' undeclared (first use in this function)
block-cloop.c:120: warning: implicit declaration of function `inflateReset'
block-cloop.c:121: error: `Z_OK' undeclared (first use in this function)
block-cloop.c:123: warning: implicit declaration of function `inflate'
block-cloop.c:123: error: `Z_FINISH' undeclared (first use in this function)
block-cloop.c:124: error: `Z_STREAM_END' undeclared (first use in this function)block-cloop.c: In function `cloop_read':
block-cloop.c:135: error: `s' undeclared (first use in this function)
block-cloop.c: In function `cloop_close':
block-cloop.c:150: error: `s' undeclared (first use in this function)
block-cloop.c:156: warning: implicit declaration of function `inflateEnd'
block-dmg.c:27:18: zlib.h: No such file or directory
block-dmg.c:49: error: syntax error before "z_stream"
block-dmg.c:49: warning: no semicolon at end of struct or union
block-dmg.c:50: warning: type defaults to `int' in declaration of `BDRVDMGState'block-dmg.c:50: warning: data definition has no type or storage class
block-dmg.c: In function `dmg_open':
block-dmg.c:78: error: `s' undeclared (first use in this function)
block-dmg.c:78: error: (Each undeclared identifier is reported only once
block-dmg.c:78: error: for each function it appears in.)
block-dmg.c:164: warning: implicit declaration of function `inflateInit'
block-dmg.c:164: error: `Z_OK' undeclared (first use in this function)
block-dmg.c: At top level:
block-dmg.c:172: error: syntax error before '*' token
block-dmg.c: In function `is_sector_in_chunk':
block-dmg.c:175: error: `chunk_num' undeclared (first use in this function)
block-dmg.c:175: error: `s' undeclared (first use in this function)
block-dmg.c:175: error: `sector_num' undeclared (first use in this function)
block-dmg.c: At top level:
block-dmg.c:182: error: syntax error before '*' token
block-dmg.c: In function `search_chunk':
block-dmg.c:185: error: `s' undeclared (first use in this function)
block-dmg.c:188: error: `sector_num' undeclared (first use in this function)
block-dmg.c: At top level:
block-dmg.c:198: error: syntax error before '*' token
block-dmg.c: In function `dmg_read_chunk':
block-dmg.c:200: error: `s' undeclared (first use in this function)
block-dmg.c:200: error: `sector_num' undeclared (first use in this function)
block-dmg.c:233: warning: implicit declaration of function `inflateReset'
block-dmg.c:234: error: `Z_OK' undeclared (first use in this function)
block-dmg.c:236: warning: implicit declaration of function `inflate'
block-dmg.c:236: error: `Z_FINISH' undeclared (first use in this function)
block-dmg.c:237: error: `Z_STREAM_END' undeclared (first use in this function)
block-dmg.c: In function `dmg_read':
block-dmg.c:257: error: `s' undeclared (first use in this function)
block-dmg.c: In function `dmg_close':
block-dmg.c:272: error: `s' undeclared (first use in this function)
block-dmg.c:283: warning: implicit declaration of function `inflateEnd'
make: *** [qemu-img] Error 1

``` 

My ./configure output is this:

 ```
$ ./configure
Install prefix	/usr/local
BIOS directory	/usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path	   /home/agent/computer/deb/qemu/qemu-0.7.0
C compiler		gcc
make			  make
host CPU		  i386
host big endian   no
target list	 i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu
gprof enabled	 no
static build	  no
SDL support	   no
mingw32 support   no
Adlib support	 no
FMOD support	  no
kqemu support	 no

``` 

I read somewhere that one should install build-essentials but the description says that it is for building deb's, something I do not need right now. Anyone have any ideas on what can be wrong?

---

### Post by syltty on 2005-05-11
auto-apt is a great tool when compiling from sources

try if this helps:
$ sudo apt-get install auto-apt
$ sudo auto-apt update
$ sudo auto-apt updatedb
$ sudo auto-apt update-local
$ auto-apt run ./configure
$ ./configure

and instead of "make install" create debian package with checkinstall:
sudo apt-get install checkinstall
sudo checkinstall

---

### Post by AgenT on 2005-05-11
[QUOTE=syltty]auto-apt is a great tool when compiling from sources
[/QUOTE]

This does not help. It wants to install packages which I *know* are not needed. Packages that, for example, are disabled in the configure script but which the configure script goes through to make sure and check whether or not they are there. I did decide to go through with letting auto-apt install what it wanted (and made sure to log the packages), but after 15 packages I quit.

Any other help would be very much appreciated!

---

### Post by AgenT on 2005-05-12
[size=5]**** SOLUTION ****[/size]

I managed to find a solution to my problem. First, there were two extra packages that I needed to apt-get: texi2html and zlib1g-dev. Second, I was not able to bybass another error that happend which seems to be a bug. It looks like there was a mistake made in making the kqemu searching script error out whether or not kqemu was enabled or disabled.

What was this solution then? CVS of course. As of 2005/05/11 the CVS version works. This is rather strange because 0.6.1 works, 0.7.0 does not, and yet CVS version (which is newer than 0.7.0, in fact, it's listed as 0.7.1 in Changelog) compiles without problem. At least at a bare minimum. As in without kqemu and any non-necessary options like SDL enabled.

---

### Post by atf487 on 2005-05-30
[QUOTE=AgenT][size=5]**** SOLUTION ****[/size]

I managed to find a solution to my problem. First, there were two extra packages that I needed to apt-get: texi2html and zlib1g-dev. Second, I was not able to bybass another error that happend which seems to be a bug. It looks like there was a mistake made in making the kqemu searching script error out whether or not kqemu was enabled or disabled.

What was this solution then? CVS of course. As of 2005/05/11 the CVS version works. This is rather strange because 0.6.1 works, 0.7.0 does not, and yet CVS version (which is newer than 0.7.0, in fact, it's listed as 0.7.1 in Changelog) compiles without problem. At least at a bare minimum. As in without kqemu and any non-necessary options like SDL enabled.[/QUOTE]

you have to enable the kernel headers. 

search for linux-headers in synaptic and pick the kernel headers for your 'uname-a'

i had the same problem. now kqemu will work :grin:

---

### Post by neongtr on 2005-06-30
I try to install qemu but have some problem.....i am a newbie in linux system, so I am in the learning mode.

 when I try to install qemu using instructions from other forum, I got this:

 root@chingasus:/home/ching/qemu-0.7.0 # ./configure
big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/ching/qemu-0.7.0
C compiler        gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu
gprof enabled     no
static build      no
SDL support       no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     no
root@chingasus:/home/ching/qemu-0.7.0 # checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: n

Installing with "make install"...

========================= Installation results ===========================
gcc -Wall -O2 -g -fno-strict-aliasing  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o dyngen dyngen.c
make: gcc: Command not found
make: *** [dyngen] Error 127

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

root@chingasus:/home/ching/qemu-0.7.0 #

Can anyone tell me where i get wrong, please?

---

### Post by neongtr on 2005-06-30
I follow the step of syltty and got is working.

 I dont know why, can anyone explain so that I learn from my mistake.

 thanks

---

### Post by manontheroot on 2005-07-10
Hello,
you can find some information here :
[http://ubuntu.sun.ac.za/wiki/index.php/QEMU](http://ubuntu.sun.ac.za/wiki/index.php/QEMU)

it seems that you don't have the following packages :
libsdl1.2-dev
zlib1g-dev

hope that'll help you

---

