---
title: "Socketmud Wont Compile"
date: 2007-11-07
forum: Packaging and Compiling Programs
---

### Post by Noodels on 2007-11-07
Hi, I've been trying to get socketmud working recently, [http://www.socketmud.dk/](http://www.socketmud.dk/) , but there's been a problem compiling :( .

```
noodels@noodels-desktop:~/socketmud/src$ make
[17:27:06] Compiling socket.c ...
In file included from socket.c:22:
mud.h:8:18: error: zlib.h: No such file or directory
In file included from socket.c:22:
mud.h:129: error: expected specifier-qualifier-list before ‘z_stream’
socket.c: In function ‘text_to_socket’:
socket.c:478: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:480: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:481: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:483: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:485: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:485: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:485: error: ‘D_SOCKET’ has no member named ‘out_compress_buf’
socket.c:487: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:489: warning: implicit declaration of function ‘deflate’
socket.c:489: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:489: error: ‘Z_SYNC_FLUSH’ undeclared (first use in this function)
socket.c:489: error: (Each undeclared identifier is reported only once
socket.c:489: error: for each function it appears in.)
socket.c:491: error: ‘Z_OK’ undeclared (first use in this function)
socket.c:495: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:495: error: ‘D_SOCKET’ has no member named ‘out_compress_buf’
socket.c:501: error: ‘D_SOCKET’ has no member named ‘out_compress_buf’
socket.c:511: error: ‘D_SOCKET’ has no member named ‘out_compress_buf’
socket.c:511: error: ‘D_SOCKET’ has no member named ‘out_compress_buf’
socket.c:513: error: ‘D_SOCKET’ has no member named ‘out_compress’
socket.c:513: error: ‘D_SOCKET’ has no member named ‘out_compress_buf’
make: *** [socket.o] Error 1
noodels@noodels-desktop:~/socketmud/src$ 

```

This makes me rather sad as every mud I look at has too many features already built in and I am at a total loss as to setting up a program that works with the internet, so this is the ideal one. I am using version 2.2. Would an earlier version work? Am I missing some sort of 'zlib.h' as mentioned in the error?

---

### Post by tehet on 2007-11-07
> **Noodels said:**
> Am I missing some sort of 'zlib.h' as mentioned in the error?
Yes. You can track down what packages contain zlib.h with apt-file or at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Noodels on 2007-11-08
Apt-file? How do I use that?

---

### Post by tehet on 2007-11-08
Just like apt-get.
```
apt-file search zlib.h
```
I this it'll spit out a lot of packages that contain zlib.h. Installing anyone of those should do I think.

---

### Post by Noodels on 2007-11-09
```
noodels@noodels-desktop:~$ apt-file search zlib.h
noodels@noodels-desktop:~$ 
```

And if I use the link mentioned the packages mentioned in the searches don't help, I've installed 1 or 2.

---

### Post by tehet on 2007-11-09
> **Noodels said:**
> ```
noodels@noodels-desktop:~$ apt-file search zlib.h
noodels@noodels-desktop:~$ 
```
Strange. You do have apt-file installed right? I get this:
```
apt-file search zlib.h
autoconf-archive: usr/share/doc/autoconf-archive/html/check_zlib.html
autoconf-archive: usr/share/doc/autoconf-archive/html/check_zlib.html
autoconf-archive: usr/share/doc/autoconf-archive/html/check_zlib.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/LFS-BOOK/appendixa/zlib.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/LFS-BOOK/appendixa/zlib.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/LFS-BOOK/appendixa/zlib.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/LFS-BOOK/chapter06/zlib.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/LFS-BOOK/chapter06/zlib.html
doc-linux-ja-html: usr/share/doc/HOWTO/ja-html/LFS-BOOK/chapter06/zlib.html
drscheme: usr/lib/plt/collects/plot/src/all/zlib.h
drscheme: usr/lib/plt/collects/plot/src/all/zlib.h
drscheme: usr/lib/plt/collects/plot/src/all/zlib.h
ecos: usr/src/ecos/packages/compat/linux/v2_0/include/linux/zlib.h
ecos: usr/src/ecos/packages/compat/linux/v2_0/include/linux/zlib.h
ecos: usr/src/ecos/packages/compat/linux/v2_0/include/linux/zlib.h
ecos: usr/src/ecos/packages/services/compress/zlib/v2_0/include/zlib.h
ecos: usr/src/ecos/packages/services/compress/zlib/v2_0/include/zlib.h
ecos: usr/src/ecos/packages/services/compress/zlib/v2_0/include/zlib.h
erlang-doc-html: usr/share/doc/erlang-doc-html/html/lib/kernel-2.11.4/doc/html/zlib.html
erlang-doc-html: usr/share/doc/erlang-doc-html/html/lib/kernel-2.11.4/doc/html/zlib.html
erlang-doc-html: usr/share/doc/erlang-doc-html/html/lib/kernel-2.11.4/doc/html/zlib.html
libboost-doc: usr/share/doc/libboost-doc/HTML/libs/iostreams/doc/classes/zlib.html
libboost-doc: usr/share/doc/libboost-doc/HTML/libs/iostreams/doc/classes/zlib.html
libboost-doc: usr/share/doc/libboost-doc/HTML/libs/iostreams/doc/classes/zlib.html
libboost-iostreams-dev: usr/include/boost/iostreams/detail/config/zlib.hpp
libboost-iostreams-dev: usr/include/boost/iostreams/detail/config/zlib.hpp
libboost-iostreams-dev: usr/include/boost/iostreams/detail/config/zlib.hpp
libboost-iostreams-dev: usr/include/boost/iostreams/filter/zlib.hpp
libboost-iostreams-dev: usr/include/boost/iostreams/filter/zlib.hpp
libboost-iostreams-dev: usr/include/boost/iostreams/filter/zlib.hpp
libbotan-dev: usr/include/botan/zlib.h
libbotan-dev: usr/include/botan/zlib.h
libbotan-dev: usr/include/botan/zlib.h
libbz2-dev: usr/include/bzlib.h
libbz2-dev: usr/include/bzlib.h
libbz2-dev: usr/include/bzlib.h
libcomplearn-dev: usr/include/complearn-1.0/complearn/complearn-rcbzlib.h
libcomplearn-dev: usr/include/complearn-1.0/complearn/complearn-rcbzlib.h
libcomplearn-dev: usr/include/complearn-1.0/complearn/complearn-rcbzlib.h
libcomplearn-dev: usr/include/complearn-1.0/complearn/complearn-rczlib.h
libcomplearn-dev: usr/include/complearn-1.0/complearn/complearn-rczlib.h
libcomplearn-dev: usr/include/complearn-1.0/complearn/complearn-rczlib.h
libcrypto++-dev: usr/include/crypto++/zlib.h
libcrypto++-dev: usr/include/crypto++/zlib.h
libcrypto++-dev: usr/include/crypto++/zlib.h
libdc0-dev: usr/include/dclib/core/czlib.h
libdc0-dev: usr/include/dclib/core/czlib.h
libdc0-dev: usr/include/dclib/core/czlib.h
libinsighttoolkit-dev: usr/include/InsightToolkit/Utilities/itk_zlib.h
libinsighttoolkit-dev: usr/include/InsightToolkit/Utilities/itk_zlib.h
libinsighttoolkit-dev: usr/include/InsightToolkit/Utilities/itk_zlib.h
libinsighttoolkit-dev: usr/include/InsightToolkit/Utilities/znzlib.h
libinsighttoolkit-dev: usr/include/InsightToolkit/Utilities/znzlib.h
libinsighttoolkit-dev: usr/include/InsightToolkit/Utilities/znzlib.h
libklibc-dev: usr/lib/klibc/include/zlib.h
libklibc-dev: usr/lib/klibc/include/zlib.h
libklibc-dev: usr/lib/klibc/include/zlib.h
libnewlib-headers: usr/include/newlib/net/zlib.h
libnewlib-headers: usr/include/newlib/net/zlib.h
libnewlib-headers: usr/include/newlib/net/zlib.h
libniftiio0-dev: usr/include/nifti/znzlib.h
libniftiio0-dev: usr/include/nifti/znzlib.h
libniftiio0-dev: usr/include/nifti/znzlib.h
libpoco-dev: usr/include/Poco/zlib.h
libpoco-dev: usr/include/Poco/zlib.h
libpoco-dev: usr/include/Poco/zlib.h
libsilc-1.1-2-dev: usr/share/doc/libsilc-1.1-2-dev/toolkit/zlib.html
libsilc-1.1-2-dev: usr/share/doc/libsilc-1.1-2-dev/toolkit/zlib.html
libsilc-1.1-2-dev: usr/share/doc/libsilc-1.1-2-dev/toolkit/zlib.html
libsword-dev: usr/include/sword/zlib.h
libsword-dev: usr/include/sword/zlib.h
libsword-dev: usr/include/sword/zlib.h
libtagcoll2-dev: usr/include/tagcoll-2.0.6/tagcoll/input/zlib.h
libtagcoll2-dev: usr/include/tagcoll-2.0.6/tagcoll/input/zlib.h
libtagcoll2-dev: usr/include/tagcoll-2.0.6/tagcoll/input/zlib.h
libuclibc-dev: usr/i386-uclibc-linux/include/linux/zlib.h
libuclibc-dev: usr/i386-uclibc-linux/include/linux/zlib.h
libuclibc-dev: usr/i386-uclibc-linux/include/linux/zlib.h
libvtk5-dev: usr/include/vtk-5.0/vtk_zlib.h
libvtk5-dev: usr/include/vtk-5.0/vtk_zlib.h
libvtk5-dev: usr/include/vtk-5.0/vtk_zlib.h
libxar-dev: usr/include/xarlib/zlib.h
libxar-dev: usr/include/xarlib/zlib.h
libxar-dev: usr/include/xarlib/zlib.h
linux-headers-2.6.22-14: usr/src/linux-headers-2.6.22-14/include/linux/zlib.h
linux-headers-2.6.22-14: usr/src/linux-headers-2.6.22-14/include/linux/zlib.h
linux-headers-2.6.22-14: usr/src/linux-headers-2.6.22-14/include/linux/zlib.h
linux-headers-2.6.22-14-386: usr/src/linux-headers-2.6.22-14-386/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-386: usr/src/linux-headers-2.6.22-14-386/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-386: usr/src/linux-headers-2.6.22-14-386/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-386: usr/src/linux-headers-2.6.22-14-386/include/linux/zlib.h
linux-headers-2.6.22-14-386: usr/src/linux-headers-2.6.22-14-386/include/linux/zlib.h
linux-headers-2.6.22-14-386: usr/src/linux-headers-2.6.22-14-386/include/linux/zlib.h
linux-headers-2.6.22-14-generic: usr/src/linux-headers-2.6.22-14-generic/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-generic: usr/src/linux-headers-2.6.22-14-generic/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-generic: usr/src/linux-headers-2.6.22-14-generic/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-generic: usr/src/linux-headers-2.6.22-14-generic/include/linux/zlib.h
linux-headers-2.6.22-14-generic: usr/src/linux-headers-2.6.22-14-generic/include/linux/zlib.h
linux-headers-2.6.22-14-generic: usr/src/linux-headers-2.6.22-14-generic/include/linux/zlib.h
linux-headers-2.6.22-14-rt: usr/src/linux-headers-2.6.22-14-rt/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-rt: usr/src/linux-headers-2.6.22-14-rt/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-rt: usr/src/linux-headers-2.6.22-14-rt/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-rt: usr/src/linux-headers-2.6.22-14-rt/include/linux/zlib.h
linux-headers-2.6.22-14-rt: usr/src/linux-headers-2.6.22-14-rt/include/linux/zlib.h
linux-headers-2.6.22-14-rt: usr/src/linux-headers-2.6.22-14-rt/include/linux/zlib.h
linux-headers-2.6.22-14-server: usr/src/linux-headers-2.6.22-14-server/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-server: usr/src/linux-headers-2.6.22-14-server/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-server: usr/src/linux-headers-2.6.22-14-server/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-server: usr/src/linux-headers-2.6.22-14-server/include/linux/zlib.h
linux-headers-2.6.22-14-server: usr/src/linux-headers-2.6.22-14-server/include/linux/zlib.h
linux-headers-2.6.22-14-server: usr/src/linux-headers-2.6.22-14-server/include/linux/zlib.h
linux-headers-2.6.22-14-ume: usr/src/linux-headers-2.6.22-14-ume/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-ume: usr/src/linux-headers-2.6.22-14-ume/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-ume: usr/src/linux-headers-2.6.22-14-ume/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-ume: usr/src/linux-headers-2.6.22-14-ume/include/linux/zlib.h
linux-headers-2.6.22-14-ume: usr/src/linux-headers-2.6.22-14-ume/include/linux/zlib.h
linux-headers-2.6.22-14-ume: usr/src/linux-headers-2.6.22-14-ume/include/linux/zlib.h
linux-headers-2.6.22-14-virtual: usr/src/linux-headers-2.6.22-14-virtual/include/linux/zlib.h
linux-headers-2.6.22-14-virtual: usr/src/linux-headers-2.6.22-14-virtual/include/linux/zlib.h
linux-headers-2.6.22-14-virtual: usr/src/linux-headers-2.6.22-14-virtual/include/linux/zlib.h
linux-headers-2.6.22-14-xen: usr/src/linux-headers-2.6.22-14-xen/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-xen: usr/src/linux-headers-2.6.22-14-xen/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-xen: usr/src/linux-headers-2.6.22-14-xen/include/config/jffs2/zlib.h
linux-headers-2.6.22-14-xen: usr/src/linux-headers-2.6.22-14-xen/include/linux/zlib.h
linux-headers-2.6.22-14-xen: usr/src/linux-headers-2.6.22-14-xen/include/linux/zlib.h
linux-headers-2.6.22-14-xen: usr/src/linux-headers-2.6.22-14-xen/include/linux/zlib.h
linux-patch-openswan: usr/src/kernel-patches/all/openswan/linux/include/zlib/zlib.h
linux-patch-openswan: usr/src/kernel-patches/all/openswan/linux/include/zlib/zlib.h
linux-patch-openswan: usr/src/kernel-patches/all/openswan/linux/include/zlib/zlib.h
lsb-build-base2: usr/include/lsb2/zlib.h
lsb-build-base2: usr/include/lsb2/zlib.h
lsb-build-base2: usr/include/lsb2/zlib.h
lsb-build-base3: usr/include/lsb3/zlib.h
lsb-build-base3: usr/include/lsb3/zlib.h
lsb-build-base3: usr/include/lsb3/zlib.h
mzscheme: usr/share/plt/doc/mzlib/mzlib.hlog
mzscheme: usr/share/plt/doc/mzlib/mzlib.hlog
mzscheme: usr/share/plt/doc/mzlib/mzlib.hlog
mzscheme: usr/share/plt/doc/mzlib/mzlib.html
mzscheme: usr/share/plt/doc/mzlib/mzlib.html
mzscheme: usr/share/plt/doc/mzlib/mzlib.html
php-doc: usr/share/doc/php-doc/html/ref.zlib.html
php-doc: usr/share/doc/php-doc/html/ref.zlib.html
php-doc: usr/share/doc/php-doc/html/ref.zlib.html
python2.4-doc: usr/share/doc/python2.4/html/lib/module-zlib.html
python2.4-doc: usr/share/doc/python2.4/html/lib/module-zlib.html
python2.4-doc: usr/share/doc/python2.4/html/lib/module-zlib.html
python2.5-doc: usr/share/doc/python2.5/html/lib/module-zlib.html
python2.5-doc: usr/share/doc/python2.5/html/lib/module-zlib.html
python2.5-doc: usr/share/doc/python2.5/html/lib/module-zlib.html
sunbird-dev: usr/include/sunbird/libbz2/bzlib.h
sunbird-dev: usr/include/sunbird/libbz2/bzlib.h
sunbird-dev: usr/include/sunbird/libbz2/bzlib.h
sunbird-dev: usr/include/sunbird/zlib/zlib.h
sunbird-dev: usr/include/sunbird/zlib/zlib.h
sunbird-dev: usr/include/sunbird/zlib/zlib.h
tex4ht-common: usr/share/texmf/tex4ht/ht-fonts/alias/arabi/nazlib.htf
tex4ht-common: usr/share/texmf/tex4ht/ht-fonts/alias/arabi/nazlib.htf
tex4ht-common: usr/share/texmf/tex4ht/ht-fonts/alias/arabi/nazlib.htf
x11proto-xext-dev: usr/include/X11/extensions/lbxzlib.h
x11proto-xext-dev: usr/include/X11/extensions/lbxzlib.h
x11proto-xext-dev: usr/include/X11/extensions/lbxzlib.h
xen-doc-2.6.16: usr/share/doc/xen-doc-2.6.16/Documentation/include/linux/zlib.h.gz
xen-doc-2.6.16: usr/share/doc/xen-doc-2.6.16/Documentation/include/linux/zlib.h.gz
xen-doc-2.6.16: usr/share/doc/xen-doc-2.6.16/Documentation/include/linux/zlib.h.gz
xen-headers-2.6.16: usr/src/xen-headers-2.6.16/include/linux/zlib.h
xen-headers-2.6.16: usr/src/xen-headers-2.6.16/include/linux/zlib.h
xen-headers-2.6.16: usr/src/xen-headers-2.6.16/include/linux/zlib.h
xen-headers-2.6.19-4: usr/src/xen-headers-2.6.19-4/include/linux/zlib.h
xen-headers-2.6.19-4: usr/src/xen-headers-2.6.19-4/include/linux/zlib.h
xen-headers-2.6.19-4: usr/src/xen-headers-2.6.19-4/include/linux/zlib.h
xen-headers-2.6.19-4-generic: usr/src/xen-headers-2.6.19-4-generic/include/config/jffs2/zlib.h
xen-headers-2.6.19-4-generic: usr/src/xen-headers-2.6.19-4-generic/include/config/jffs2/zlib.h
xen-headers-2.6.19-4-generic: usr/src/xen-headers-2.6.19-4-generic/include/config/jffs2/zlib.h
xen-headers-2.6.19-4-generic: usr/src/xen-headers-2.6.19-4-generic/include/linux/zlib.h
xen-headers-2.6.19-4-generic: usr/src/xen-headers-2.6.19-4-generic/include/linux/zlib.h
xen-headers-2.6.19-4-generic: usr/src/xen-headers-2.6.19-4-generic/include/linux/zlib.h
xen-headers-2.6.19-4-server: usr/src/xen-headers-2.6.19-4-server/include/config/jffs2/zlib.h
xen-headers-2.6.19-4-server: usr/src/xen-headers-2.6.19-4-server/include/config/jffs2/zlib.h
xen-headers-2.6.19-4-server: usr/src/xen-headers-2.6.19-4-server/include/config/jffs2/zlib.h
xen-headers-2.6.19-4-server: usr/src/xen-headers-2.6.19-4-server/include/linux/zlib.h
xen-headers-2.6.19-4-server: usr/src/xen-headers-2.6.19-4-server/include/linux/zlib.h
xen-headers-2.6.19-4-server: usr/src/xen-headers-2.6.19-4-server/include/linux/zlib.h
zlib1g-dev: usr/include/zlib.h
zlib1g-dev: usr/include/zlib.h
zlib1g-dev: usr/include/zlib.h
```

[quote]And if I use the link mentioned the packages mentioned in the searches don't help, I've installed 1 or 2.
Also wierd. I assume you used this list?
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=zlib.h&searchmode=searchfiles&case=insensitive&version=gutsy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=zlib.h&searchmode=searchfiles&case=insensitive&version=gutsy&arch=i386)
I'd go for zlib1g-dev or something as it sounds the most logical. But from my limited compiling experience installing any package that contains the missing file has always resolved compiler errors such as the one you described.

---

### Post by Noodels on 2007-11-09
As looking through the suggested list and amd64 list I found the mentioned file and just this minute installed it, no difference to the compile, don't know if I'll be ridiculed for trying but I'm going to find the zlib.h file and copy it to the directory.

---

### Post by tehet on 2007-11-09
Noodles,
I tried it myself, here's the output:
```
~/sokmud/socketmud/src$ make
[23:58:22] Compiling socket.c ...
In file included from socket.c:22:
mud.h:8:18: error: zlib.h: No such file or directory
In file included from socket.c:22:
mud.h:129: error: expected specifier-qualifier-list before &#8216;z_stream&#8217;
socket.c: In function &#8216;text_to_socket&#8217;:
socket.c:478: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:480: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:481: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:483: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:485: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:485: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:485: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress_buf&#8217;
socket.c:487: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:489: warning: implicit declaration of function &#8216;deflate&#8217;
socket.c:489: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:489: error: &#8216;Z_SYNC_FLUSH&#8217; undeclared (first use in this function)
socket.c:489: error: (Each undeclared identifier is reported only once
socket.c:489: error: for each function it appears in.)
socket.c:491: error: &#8216;Z_OK&#8217; undeclared (first use in this function)
socket.c:495: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:495: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress_buf&#8217;
socket.c:501: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress_buf&#8217;
socket.c:511: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress_buf&#8217;
socket.c:511: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress_buf&#8217;
socket.c:513: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress&#8217;
socket.c:513: error: &#8216;D_SOCKET&#8217; has no member named &#8216;out_compress_buf&#8217;
make: *** [socket.o] Error 1
~/sokmud/socketmud/src$ sudo apt-get install zlib1g-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  zlib1g-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 160kB of archives.
After unpacking 385kB of additional disk space will be used.
Get:1 http://nl.archive.ubuntu.com gutsy/main zlib1g-dev 1:1.2.3.3.dfsg-5ubuntu2 [160kB]
Fetched 160kB in 0s (1661kB/s)
Selecting previously deselected package zlib1g-dev.
(Reading database ... 87288 files and directories currently installed.)
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.3.dfsg-5ubuntu2_i386.deb) ...
Setting up zlib1g-dev (1:1.2.3.3.dfsg-5ubuntu2) ...
~/sokmud/socketmud/src$ make
[23:59:31] Compiling socket.c ...
[23:59:31] Compiling io.c ...
[23:59:31] Compiling strings.c ...
[23:59:31] Compiling utils.c ...
[23:59:31] Compiling interpret.c ...
[23:59:31] Compiling help.c ...
[23:59:32] Compiling action_safe.c ...
[23:59:32] Compiling mccp.c ...
[23:59:32] Compiling save.c ...
[23:59:32] Compiling event.c ...
[23:59:32] Compiling event-handler.c ...
[23:59:32] Compiling list.c ...
[23:59:32] Compiling stack.c ...
rm -f SocketMud
gcc -o SocketMud socket.o io.o strings.o utils.o interpret.o help.o action_safe.o mccp.o save.o event.o event-handler.o list.o stack.o -lz -lpthread -lcrypt
~/sokmud/socketmud/src$
```
Perhaps there's a clue in there that can help you further. Btw, I'm on i386, not 64_x86 and I don't know if that makes a big difference. Other than that I don't know how to help you further. Good luck!

---

### Post by Noodels on 2007-11-10
Okay, I'm trying the -dev one now. I probably should have tried it yesterday.

---

### Post by Noodels on 2007-11-10
Excellent! It worked! I'll probably run straight into another problem but progress is progress.

EDIT: Here it is, I was expecting there to be a folder containing all the verbs or something but the only verbs are built into the source code I compiled. Gah.

---

