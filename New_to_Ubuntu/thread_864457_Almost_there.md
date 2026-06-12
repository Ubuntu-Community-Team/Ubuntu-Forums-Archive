---
title: "Almost there"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by rab4567 on 2008-07-19
OK I'm putting ubuntu on this kids laptop I and got everything running including broadcom stuff, but now there is error when I downloaded dvd read codec seen here


No prebuilt binary available.  Will try to build and install it.
You need to have debhelper and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed

--15:33:18--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5.orig.tar.gz)
           => `libdvdcss_1.2.5.orig.tar.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se|129.16.30.198|:80](www.dtek.chalmers.se|129.16.30.198|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 267,699 (261K) [application/x-tar]

100%[====================================>] 267,699      123.52K/s             

15:33:21 (123.27 KB/s) - `libdvdcss_1.2.5.orig.tar.gz' saved [267699/267699]

--15:33:21--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.diff.gz)
           => `libdvdcss_1.2.5-1.diff.gz'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se|129.16.30.198|:80](www.dtek.chalmers.se|129.16.30.198|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 20 [text/plain]

100%[====================================>] 20            --.--K/s             

15:33:21 (777.46 KB/s) - `libdvdcss_1.2.5-1.diff.gz' saved [20/20]

--15:33:21--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss_1.2.5-1.dsc)
           => `libdvdcss_1.2.5-1.dsc'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se|129.16.30.198|:80](www.dtek.chalmers.se|129.16.30.198|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 341 [text/plain]

100%[====================================>] 341           --.--K/s             

15:33:22 (276.03 KB/s) - `libdvdcss_1.2.5-1.dsc' saved [341/341]

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
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

can anyone help me this kid really loves compiz I know its experimental but I need the help. His laptop is a HP pavilion dv 6000 80HB 2GB ram amd 64 x2

---

### Post by spiderbatdad on 2008-07-19
```
sudo apt-get install build-essential debhelper fakeroot
```

---

### Post by daimaru on 2008-07-19
did u install 8.04? even 7.10 has compiz fusion preinstalled. so just install either compiz-fusion-settings-manager or the other one thats called simple settings something manager. Sorry cant remember the right names for the packages, but just search for compiz and you will find it. Then just enable all the stuff you want under preferences -> advanced settings.... and your compiz fusion stuff is working. 

sorry using windows right now so i could not lookup the right names but setting up compiz fusion is a breeze in 7.10 and 8.04 you dont need to compile it form source. and compiz has merged with compiz fusion which means you would be installing some older version if you did download compiz form some location.

---

### Post by rab4567 on 2008-07-19
The debhelper and the fakeroot did not work as for compiz every thing is working fine I just can;t play dvds on hardy 8.0.4.1 64

---

### Post by arpanaut on 2008-07-19
Take a look at this page,,
DVD play item #6

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

