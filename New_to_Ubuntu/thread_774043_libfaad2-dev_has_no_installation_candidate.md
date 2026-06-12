---
title: "libfaad2-dev has no installation candidate"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by gll on 2008-04-29
I'm trying to get 'ffmpeg' working. I had it installed, but without mp3 or lame support, so it was working only without audio support. I've uninstalled ffmpeg and I'm trying to reinstall from informations posted here: ([https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)), but it failed to install **libfaad2-dev**.

Using **libfaad-dev**, I won't be able to **--enable-vorbis** with **./configure**.

I don't know where to look at...

[LIST=1]
[*]Conflict with something else installed
[*]Not Available on Hardy Heron yet
[*]Wrong Packages sources
[/LIST]

(I've few packages sources activated (Multiverse, universe,...). I even tried with libfaad-dev, but it doesn't work.
```
goo@gll:/media/GOO/tmp$ sudo apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
goo@gll:/media/GOO/tmp$ sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libdts-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liblame-dev is already the newest version.
Package libfaad2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libfaad-dev
E: Package libfaad2-dev has no installation candidate

```

I'm using Ubuntu Heron (updated last week) on a duo-core (32bits). I'm not familiar with compiling install.

---

### Post by Seisen on 2008-04-29
> **gll said:**
> I'm trying to get 'ffmpeg' working. I had it installed, but without mp3 or lame support, so it was working only without audio support. I've uninstalled ffmpeg and I'm trying to reinstall from informations posted here: ([https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)), but it failed to install **libfaad2-dev**.

Using **libfaad-dev**, I won't be able to **--enable-vorbis** with **./configure**.

I don't know where to look at...

[LIST=1]
[*]Conflict with something else installed
[*]Not Available on Hardy Heron yet
[*]Wrong Packages sources
[/LIST]

(I've few packages sources activated (Multiverse, universe,...). I even tried with libfaad-dev, but it doesn't work.
```
goo@gll:/media/GOO/tmp$ sudo apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
goo@gll:/media/GOO/tmp$ sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libdts-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liblame-dev is already the newest version.
Package libfaad2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libfaad-dev
E: Package libfaad2-dev has no installation candidate

```

I'm using Ubuntu Heron (updated last week) on a duo-core (32bits). I'm not familiar with compiling install.

Here is a link to the deb file you can download and install by either double-clicking on the file or using terminal. [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libfaad-dev]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libfaad-dev")

```
sudo dpkg -i libfaad-dev
```

---

### Post by gll on 2008-04-29
Thank you very much for your reply..
I tried this, but it doesn't seems to solve anything.

I'm posting the logs that I get, so you could understand the process. (I'm sorry if it's long, I think it might be better to understand).




Installing **libfaad-dev** instead of **libfaad2-dev** from the link above:
```
goo@gll:/media/GOO/tmp$ sudo dpkg -i libfaad-dev_2.6.1-2_i386.deb 
(Reading database ... 139692 files and directories currently installed.)
Preparing to replace libfaad-dev 2.6.1-2 (using libfaad-dev_2.6.1-2_i386.deb) ...
Unpacking replacement libfaad-dev ...
Setting up libfaad-dev (2.6.1-2) ...
```


Continue the process described here: ([https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg))
```
goo@gll:/media/GOO/tmp$ sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libdts-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liblame-dev is already the newest version.
Package libfaad2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libfaad-dev
E: Package libfaad2-dev has no installation candidate
```

It fail for libfaad2-dev. Then I removed the libfaad2-dev from the install line:
```
goo@gll:/media/GOO/tmp$ sudo apt-get install liblame-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libdts-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liblame-dev is already the newest version.
libfaac-dev is already the newest version.
libxvidcore4-dev is already the newest version.
liba52-0.7.4 is already the newest version.
liba52-0.7.4-dev is already the newest version.
libdts-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

ok, Now, get the source for ffmpeg:
```
goo@gll:/media/GOO/tmp$ apt-get source ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2633kB of source archives.
Get:1 http://ch.archive.ubuntu.com hardy/main ffmpeg 3:0.cvs20070307-5ubuntu7 (dsc) [1283B]
Get:2 http://ch.archive.ubuntu.com hardy/main ffmpeg 3:0.cvs20070307-5ubuntu7 (tar) [2593kB]
Get:3 http://ch.archive.ubuntu.com hardy/main ffmpeg 3:0.cvs20070307-5ubuntu7 (diff) [38.7kB]
Fetched 2633kB in 2s (899kB/s)
gpg: Signature made Wed 12 Mar 2008 02:45:44 PM CET using DSA key ID DDCD686A
gpg: Can't check signature: public key not found
dpkg-source: extracting ffmpeg in ffmpeg-0.cvs20070307
dpkg-source: unpacking ffmpeg_0.cvs20070307.orig.tar.gz
dpkg-source: applying ./ffmpeg_0.cvs20070307-5ubuntu7.diff.gz
goo@gll:/media/GOO/tmp$ 

```

Trying to configure, but it failed..
```
goo@gll:/media/GOO/tmp$ cd ffmpeg-*/
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ ./configure --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-shared
Unknown option "--enable-vorbis".
See ./configure --help for available options.
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ 
```

Ok, let's remove all those who are not working (even mp3Lame)...
```
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ ./configure --enable-gpl --enable-pp --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-shared
Unknown option "--enable-a52".
See ./configure --help for available options.
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ ./configure --enable-gpl --enable-pp --enable-libogg --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-sharedUnknown option "--enable-dts".
See ./configure --help for available options.
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ ./configure --enable-gpl --enable-pp --enable-libogg --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-shared
Unknown option "--enable-mp3lame".
See ./configure --help for available options.
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ ./configure --enable-gpl --enable-pp --enable-libogg --enable-dc1394 --enable-libgsm --disable-debug --enable-faad --enable-faac --enable-xvid --enable-shared
Unknown option "--enable-faad".
See ./configure --help for available options.
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ ./configure --enable-gpl --enable-pp --enable-libogg --enable-dc1394 --enable-libgsm --disable-debug --enable-faac --enable-xvid --enable-shared
Unknown option "--enable-faac".
See ./configure --help for available options.
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ ./configure --enable-gpl --enable-pp --enable-libogg --enable-dc1394 --enable-libgsm --disable-debug --enable-xvid --enable-shared
install prefix            /usr/local
source path               /media/GOO/tmp/ffmpeg-0.cvs20070307
C compiler                gcc
make                      make
.align is power-of-two    no
ARCH                      x86_32 (generic)
big-endian                no
MMX enabled               yes
CMOV enabled              no
CMOV is fast              no
gprof enabled             no
debug symbols             no
strip symbols             yes
optimize                  yes
static                    yes
shared                    yes
postprocessing support    yes
software scaler enabled   no
video hooking             yes
Imlib2 support            yes
FreeType support          yes
network support           yes
IPv6 support              yes
threading support         no
SDL support               yes
Sun medialib support      no
AVISynth enabled          no
liba52 support            no
liba52 dlopened           no
libdts support            no
libfaac enabled           no
libfaad enabled           no
faadbin enabled           no
libgsm enabled            yes
libmp3lame enabled        no
libnut enabled            no
libogg enabled            yes
libtheora enabled         no
libvorbis enabled         no
x264 enabled              no
XviD enabled              yes
zlib enabled              yes
AMR-NB float support      no
AMR-NB fixed support      no
AMR-WB float support      no
AMR-WB IF2 support        no
License: GPL
Creating config.mak and config.h...
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ 

```

End up with make, with a tons of warnings and ffmpeg is not working at the end:
```
cp -p ffmpeg_g ffmpeg
strip ffmpeg
gcc -fomit-frame-pointer -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3 -I"/media/GOO/tmp/ffmpeg-0.cvs20070307" -I"/media/GOO/tmp/ffmpeg-0.cvs20070307" -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavutil -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavcodec -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavformat -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libswscale -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -c -o ffplay.o ffplay.c
In file included from /media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat/avformat.h:36,
                 from ffplay.c:22:
/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec/avcodec.h:2439: warning: &#8216;ImgReSampleContext&#8217; is deprecated
/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec/avcodec.h:2442: warning: &#8216;ImgReSampleContext&#8217; is deprecated
In file included from ffplay.c:22:
/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat/avformat.h:282: warning: &#8216;AVFrac&#8217; is deprecated
ffplay.c: In function &#8216;audio_decode_frame&#8217;:
ffplay.c:1559: warning: &#8216;avcodec_decode_audio&#8217; is deprecated (declared at /media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec/avcodec.h:2722)
gcc -L"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavformat -L"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavcodec -L"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavutil -Wl,--warn-common  -rdynamic -export-dynamic -Wl,--as-needed -Wl,-rpath-link,"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavcodec -Wl,-rpath-link,"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavformat -Wl,-rpath-link,"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavutil -g -o ffplay_g ffplay.o cmdutils.o -lavformat -lavcodec -lavutil -lm -lz -lgsm -logg -lxvidcore -ldc1394_control -lraw1394 -ldl    -L/usr/lib -lSDL
cp -p ffplay_g ffplay
strip ffplay
gcc -fomit-frame-pointer -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3 -I"/media/GOO/tmp/ffmpeg-0.cvs20070307" -I"/media/GOO/tmp/ffmpeg-0.cvs20070307" -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavutil -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavcodec -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavformat -I"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libswscale -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -c -o ffserver.o ffserver.c
In file included from /media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat/avformat.h:36,
                 from ffserver.c:22:
/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec/avcodec.h:2439: warning: &#8216;ImgReSampleContext&#8217; is deprecated
/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec/avcodec.h:2442: warning: &#8216;ImgReSampleContext&#8217; is deprecated
In file included from ffserver.c:22:
/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat/avformat.h:282: warning: &#8216;AVFrac&#8217; is deprecated
ffserver.c: In function &#8216;main&#8217;:
ffserver.c:4302: warning: &#8216;acl.next&#8217; is used uninitialized in this function
ffserver.c:4257: note: &#8216;acl.next&#8217; was declared here
ffserver.c:4257: warning: &#8216;acl.action&#8217; may be used uninitialized in this function
ffserver.c:4257: note: &#8216;acl.action&#8217; was declared here
ffserver.c:4257: warning: &#8216;acl.first.s_addr&#8217; may be used uninitialized in this function
ffserver.c:4257: note: &#8216;acl.first.s_addr&#8217; was declared here
ffserver.c:4257: warning: &#8216;acl.last.s_addr&#8217; may be used uninitialized in this function
ffserver.c:4257: note: &#8216;acl.last.s_addr&#8217; was declared here
gcc -L"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavformat -L"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavcodec -L"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavutil -Wl,--warn-common  -rdynamic -export-dynamic -Wl,--as-needed -Wl,-rpath-link,"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavcodec -Wl,-rpath-link,"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavformat -Wl,-rpath-link,"/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavutil -g -Wl,-E -o ffserver ffserver.o -lavformat -lavcodec -lavutil -lm -lz -lgsm -logg -lxvidcore -ldc1394_control -lraw1394 -ldl   
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$ sudo make install
make -C vhook install
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/vhook'
install -d "/usr/local/lib/vhook"
install -m 755 null.so fish.so ppm.so watermark.so imlib2.so drawtext.so "/usr/local/lib/vhook"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/vhook'
install -d "/usr/local/man/man1"
install -m 644 doc/ffmpeg.1 doc/ffplay.1 doc/ffserver.1 "/usr/local/man/man1"
make -C libavutil   all
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec'
make -C libavformat all
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat'
make -C libpostproc all
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libpostproc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libpostproc'
make -C libavutil   install-libs
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil'
install -d "/usr/local/lib"
install -m 755 libavutil.so "/usr/local/lib/libavutil.so.49.3.0"
strip "/usr/local/lib/libavutil.so.49.3.0"
cd "/usr/local/lib" && \
		ln -sf libavutil.so.49.3.0 libavutil.so.49
cd "/usr/local/lib" && \
		ln -sf libavutil.so.49.3.0 libavutil.so
install -d "/usr/local/lib"
install -m 644 libavutil.a "/usr/local/lib"
ranlib "/usr/local/lib/libavutil.a"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil'
make -C libavcodec  install-libs
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec'
install -d "/usr/local/lib"
install -m 755 libavcodec.so "/usr/local/lib/libavcodec.so.51.38.0"
strip "/usr/local/lib/libavcodec.so.51.38.0"
cd "/usr/local/lib" && \
		ln -sf libavcodec.so.51.38.0 libavcodec.so.51
cd "/usr/local/lib" && \
		ln -sf libavcodec.so.51.38.0 libavcodec.so
install -d "/usr/local/lib"
install -m 644 libavcodec.a "/usr/local/lib"
ranlib "/usr/local/lib/libavcodec.a"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec'
make -C libavformat install-libs
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat'
install -d "/usr/local/lib"
install -m 755 libavformat.so "/usr/local/lib/libavformat.so.51.10.0"
strip "/usr/local/lib/libavformat.so.51.10.0"
cd "/usr/local/lib" && \
		ln -sf libavformat.so.51.10.0 libavformat.so.51
cd "/usr/local/lib" && \
		ln -sf libavformat.so.51.10.0 libavformat.so
install -d "/usr/local/lib"
install -m 644 libavformat.a "/usr/local/lib"
ranlib "/usr/local/lib/libavformat.a"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat'
make -C libpostproc install-libs
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libpostproc'
install -d "/usr/local/lib"
install -m 755 libpostproc.so "/usr/local/lib/libpostproc.so.51.1.0"
strip "/usr/local/lib/libpostproc.so.51.1.0"
cd "/usr/local/lib" && \
		ln -sf libpostproc.so.51.1.0 libpostproc.so.51
cd "/usr/local/lib" && \
		ln -sf libpostproc.so.51.1.0 libpostproc.so
install -d "/usr/local/lib"
install -m 644 libpostproc.a "/usr/local/lib"
ranlib "/usr/local/lib/libpostproc.a"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libpostproc'
ldconfig
install -d "/usr/local/bin"
install -c -m 755 ffmpeg ffplay ffserver "/usr/local/bin"
make -C libavutil   install-headers
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil'
install -d "/usr/local/include/ffmpeg"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/avutil.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/common.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/mathematics.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/integer.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/rational.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/intfloat_readwrite.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/md5.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/adler32.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/log.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/fifo.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/lzo.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil"/random.h "/usr/local/include/ffmpeg"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavutil.pc "/usr/local/lib/pkgconfig"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavutil'
make -C libavcodec  install-headers
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec'
install -d "/usr/local/include/ffmpeg"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec"/avcodec.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec"/opt.h "/usr/local/include/ffmpeg"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavcodec.pc "/usr/local/lib/pkgconfig"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavcodec'
make -C libavformat install-headers
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat'
install -d "/usr/local/include/ffmpeg"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat"/avformat.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat"/avio.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat"/rtp.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat"/rtsp.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat"/rtspcodes.h "/usr/local/include/ffmpeg"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307"/libavformat.pc "/usr/local/lib/pkgconfig"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libavformat'
make -C libpostproc install-headers
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libpostproc'
install -d "/usr/local/include/postproc"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307/libpostproc"/postprocess.h "/usr/local/include/postproc"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307"/libpostproc.pc "/usr/local/lib/pkgconfig"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libpostproc'
make -C libswscale  install-headers
make[1]: Entering directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libswscale'
install -d "/usr/local/include/ffmpeg"
install -d "/usr/local/lib/pkgconfig"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307/libswscale"/swscale.h "/media/GOO/tmp/ffmpeg-0.cvs20070307/libswscale"/rgb2rgb.h "/usr/local/include/ffmpeg"
install -m 644 "/media/GOO/tmp/ffmpeg-0.cvs20070307"/libswscale.pc "/usr/local/lib/pkgconfig"
make[1]: Leaving directory `/media/GOO/tmp/ffmpeg-0.cvs20070307/libswscale'
goo@gll:/media/GOO/tmp/ffmpeg-0.cvs20070307$

```

Is those warning related to **libfaad2-dev**?

---

### Post by gll on 2008-04-29
I reinstalled **ffmpeg** from **synaptic**.

Here is my original problem:
```
goo@gll:/media/GOO/tmp/iriver-h300-sim-w32/archos/udmurt_x_/flv$ ls
_.flv  mkvid-ffmpeg.sh  myVideo2.flv  myVideo.flv
goo@gll:/media/GOO/tmp/iriver-h300-sim-w32/archos/udmurt_x_/flv$ ffmpeg -i myVideo.flv -s 220x166 -vcodec mpeg2video -b 200k -ab 64k -ac 2 -ar 44100 -acodec mp3 myVideo.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'myVideo.flv':
  Duration: 00:04:59.9, start: 0.000000, bitrate: 8 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240, 29.92 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 8 kb/s
Output #0, mpeg, to 'myVideo.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 220x166, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
goo@gll:/media/GOO/tmp/iriver-h300-sim-w32/archos/udmurt_x_/flv$ 

```

mp3 codec is not working. How could I enable mp3 encoding? Is possible that I use a wrong codec name?

---

### Post by gll on 2008-04-29
This link ([https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)) doesn't worked for me but 
**[http://www.programmingtalk.com/showthread.php?t=31096](http://www.programmingtalk.com/showthread.php?t=31096)** worked. The configure line worked:

> ```
**./configure --enable-gpl --enable-pp --enable-libvorbis --enable-libogg  --enable-liba52 --enable-libmp3lame --enable-libfaad --enable-libfaac**
```

---

