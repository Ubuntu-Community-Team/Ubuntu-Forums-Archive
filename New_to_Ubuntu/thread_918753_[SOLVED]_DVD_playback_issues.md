---
title: "[SOLVED] DVD playback issues"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by simon303 on 2008-09-13
I am trying to get DVDs to play on my computer and have installed VLC and followed the instuctions for hardy at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").
When I play a DVD it is scrambled (see screenshot) the exits after less than a minute, however it can display the menu alright.
I noticed an error at the end of the output when I ran "install-css.sh". Here is the output
```
simon@simons-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

--14:13:54--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz
           => `libdvdcss_1.2.5.orig.tar.gz'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 267,699 (261K) [application/x-tar]

100%[====================================>] 267,699      228.88K/s             

14:13:56 (228.45 KB/s) - `libdvdcss_1.2.5.orig.tar.gz' saved [267699/267699]

--14:13:56--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz
           => `libdvdcss_1.2.5-1.diff.gz'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20 [text/plain]

100%[====================================>] 20            --.--K/s             

14:13:56 (1.83 MB/s) - `libdvdcss_1.2.5-1.diff.gz' saved [20/20]

--14:13:56--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc
           => `libdvdcss_1.2.5-1.dsc'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 341 [text/plain]

100%[====================================>] 341           --.--K/s             

14:13:56 (33.05 MB/s) - `libdvdcss_1.2.5-1.dsc' saved [341/341]

dpkg-source: warning: extracting unsigned source package (./libdvdcss_1.2.5-1.dsc)
dpkg-source: extracting libdvdcss in libdvdcss-1.2.5
dpkg-source: unpacking libdvdcss_1.2.5.orig.tar.gz
dpkg-source: applying ./libdvdcss_1.2.5-1.diff.gz
dh_testdir
./configure --prefix=/usr --mandir=${prefix}/share/man \
		--infodir=${prefix}/share/info
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77
```
Any suggestions??
Thanks

---

### Post by northern lights on 2008-09-13
Do you have a C compiler installed in the first place?

Install the meta-package 'build-essential', thereafter the script should execute correctly.

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by simon303 on 2008-09-13
Thanks, once I installed "build essential" the script ran fully and now DVDs play.

---

### Post by northern lights on 2008-09-13
Sorted.

As an aside, you can mark this thread as solved under 'Thread Tools' (upper right).

---

