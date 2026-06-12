---
title: "libdts not linking on ZoneMinder build (undefiend reference)"
date: 2006-06-11
forum: Packaging and Compiling Programs
---

### Post by dfaulkner on 2006-06-11
Hi All, I'm trying to build ZoneMinder on Ubuntu (my first zm build and my first on ubuntu). I'm a long-time Linux hack, but I've new to the world of video codecs.

[CENTER]**:idea:Update: see my [reply]("http://ubuntuforums.org/showthread.php?p=1127342#post1127342") to this post for my solution.**
[/CENTER]
 
This is the last command executed by make (wrapped for convenience), along with the error(s) I get:
```
g++  -g -O3 -march=pentium4  -L/usr/lib -L/usr/lib/mysql  \
-ldc1394_control -logg -ldts -lvorbisenc -ltheora -lgsm \
-o zmc  zmc.o zm.o zm_db.o zm_config.o zm_coord.o zm_box.o zm_poly.o  \
zm_image.o zm_event.o zm_zone.o zm_camera.o zm_local_camera.o  \
zm_remote_camera.o zm_file_camera.o zm_monitor.o zm_user.o zm_mpeg.o \
zm_jpeg.o zm_regexp.o zm_signal.o zm_buffer.o zm_debug.o  \
-lavformat -lavcodec -lavutil -lpcre -lcrypto -lmysqlclient -ldl -lz -ljpeg

/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_init': undefined reference to `dts_init'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_frame'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_blocks_num'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_block'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_samples'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_blocks_num'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame': undefined reference to `dts_syncinfo'
collect2: ld returned 1 exit status
``` 
I believe I've specified all the correct libraries. For completeness, here is the configure command I'm using:

```

./configure \
--with-webdir=/var/www/zm/html \
--with-cgidir=/var/www/zm/cgi \
--with-webuser=www-data \
--with-webgroup=www-data \
--with-extralibs="-ldc1394_control -logg -ldts -lvorbisenc -ltheora -lgsm" \
CFLAGS="-g -O3 -march=pentium4" \
CXXFLAGS="-g -O3 -march=pentium4" \
ZM_DB_NAME=zm \
ZM_DB_USER=zm \
ZM_DB_PASS=*******

``` 
I've installed the build-essential package and the following packages that I believe are needed by Zone Minder:
```

libmysqlclient15-dev # mysql client headers
libjpeg62 libjpeg-progs libjpeg62-dev # JPEG libraries and development files
ffmpeg ffmpeg2theora libfreetype6-dev libavcodec-dev libavformat-dev # MPEG video encoding.
libssl-dev openssl libssl0.9.8-dbg libssl0.9.8 # because the docs said I'd need SSL
libpcre3 libpcre3-dev # because configure complained.
libdate-manip-perl # for Date::Manip
libwww-perl libio-socket-ssl-perl libmailtools-perl libhtml-format-perl libcompress-zlib-perl # for LWP and associated libraries
libdevice-serialport-perl # for RS232 PTZ control
libarchive-tar-perl libarchive-zip-perl # for automatic event uploading
libmime-perl libmime-lite-perl # for automatic event email notification

``` 
Configure still complains about a missing X10::ActiveHome perl module but (1) it's not packaged within ubuntu, and (2) I don't need it.

I tried to install the following packages, but they were already installed:
```
libdc1394-dev libogg-dev libvorbis-dev libtheora-dev libgsm1-dev libdts-dev
``` 
My first attempt at the build was without the --with-extralibs option passed to configure. As you might imagine, the linker errors were much longer. After I added in the extralibs, including -ldts, Every other undefined reference error went away, but the errors relating to libdts remain.

I've checked /usr/lib/libdts.a and /usr/lib/libdts_pic.a with nm, and I get exactly what I expect (output below edited for length):
```

$ nm /usr/lib/libdts.a
parse.o:
[...]
00003bbe T dts_block
0000000b T dts_blocks_num
00000000 r dts_channels
         U dts_downmix
         U dts_downmix_init
0000020a T dts_dynrng
00000798 T dts_frame
00000235 T dts_free
00000020 T dts_init
000000a0 r dts_sample_rates
00000000 T dts_samples
000016b2 T dts_subframe_footer
000017f3 T dts_subframe_header
00002a19 T dts_subsubframe
00000654 T dts_syncinfo
[...]

``` 
I see no reason why I shouldn't be able to link against /usr/lib/libdts.a. :confused:Am I missing something obvious? Thanks very much for any assistance you can offer.

---

### Post by dfaulkner on 2006-06-11
Well, that was a fast one.

It turns out that what's really necessary are the shared object files (in this case /usr/lib/libtds.so.*) not /usr/lib/libtds.a. Here's what's going on:

ZoneMinder provides a configure option called '--with-extralibs' This allows one to specify extra *shared libs*, but *not static* libs. All of the other codec's provide both shared and static libraries. It turns out that there is no libtds0 or similar equivilent to libtds-dev.

I did some digging on this, and I came across [Debian Bug #285590]("http://www.archivum.info/debian-bugs-dist.lists.debian.org/2004-12/msg05878.html"), which sheds some light:
> 
>* libdts-dev is missing a shared library version of libdts.  Can you please*
>* include one?  This is important for architectures such as amd64 when*
>* linking other shared libs against libdts.*

   I will not provide a shared library because the API is not stable. If
your other shared library is a plugin, link it with -ldts_pic. If it is
a real shared library, link the executable with -ldts and use -rdynamic.
 
This appears to be the problem. I also came across a [thread]("http://www.zoneminder.com/forums/viewtopic.php?t=5576&start=0&postdays=0&postorder=asc&highlight=") in the  zoneminder forum which contains the fix that I eventually used. The solution is to proceed as I have described, with one addition:

In the ZoneMinder source tree, edit /src/Makefile (after it is made by configure). Find the LIBS= line:

```
LIBS = -lavformat -lavcodec -lavutil -lpcre -lcrypto -lmysqlclient -ldl -lz -ljpeg
``` 
and add -ldts to the end.

```
LIBS = -lavformat -lavcodec -lavutil -lpcre -lcrypto -lmysqlclient -ldl -lz -ljpeg -ldts
``` 
You will notice the EXTRA_LIBS above, that only affects .so's.

As I said on the ZoneMinder forum, I'm sure there's a cleaner way to do this, but I'm more interested in making sure my hardware works at the moment.

So, how big an issue is this missing shared lib? (is anyone else affected?)
Thanks.

---

### Post by AxelF on 2006-09-23
Thanks for this tip.  Solved my problem trying to build Zoneminder 1.22.2 on Dapper 6.06.

---

### Post by Intangir on 2006-10-23
ya thx from me too
also trying to build zone minder 1.22.2, on 6.06

i needed more libs though, im gonna list all mine incase anyone else happens across this thread like i did

-lavformat -lavcodec -lavutil -lvorbis -ltheora -logg -lgsm -ldc1394_control -ldts -lvorbisenc -lpcre -lcrypto -lmysqlclient -ldl -lz -ljpeg

---

