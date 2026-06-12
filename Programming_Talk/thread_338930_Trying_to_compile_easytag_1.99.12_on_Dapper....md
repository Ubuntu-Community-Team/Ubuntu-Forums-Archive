---
title: "Trying to compile easytag 1.99.12 on Dapper..."
date: 2007-01-15
forum: Programming Talk
---

### Post by mmcmonster on 2007-01-15
Hi.
  Please excuse me if this is the wrong forum.
  I'm trying to compile easytag 1.99.12 with mp3 support on Dapper.
  I first compiled id3lib v3.8.3  and installed it into /usr/local/lib.  I made sure /usr/local/lib was in /etc/ld.so.conf and ran ldconfig.
  When I then compiled easytag, mp3 support was disabled.
  Here is part of the output of ./configure:
```

checking for library containing ID3Tag_Link... no
configure: WARNING: id3lib not found
checking for id3lib version... configure: WARNING: could not determine id3lib version
checking for MP3 file support... no
***
*** Warning: MP3 file support disabled, id3lib missing
***

```Meanwhile, I definitely have made the libid3 library:
```

dapper:/usr/local/lib$ ls
libexo-0.3.a         libid3.la           libthunar-vfs-1.so        pkgconfig
libexo-0.3.la        libid3.so           libthunar-vfs-1.so.2      python2.4
libexo-0.3.so        libmad.a            libthunar-vfs-1.so.2.2.1  site_ruby
libexo-0.3.so.0      libmad.la           libthunarx-1.la           thunarx-1
libexo-0.3.so.0.3.1  libmad.so           libthunarx-1.so           vhook
libid3-3.8.so.3      libmad.so.0         libthunarx-1.so.2
libid3-3.8.so.3.0.0  libmad.so.0.2.1     libthunarx-1.so.2.2.1
libid3.a             libthunar-vfs-1.la  perl
dapper:/usr/local/lib$

```And here is part of `sudo make`
```

        then mv -f ".deps/mpeg_header.Tpo" ".deps/mpeg_header.Po"; else rm -f ".deps/mpeg_header.Tpo"; exit 1; fi
if gcc-3.4 -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALE=\"/usr/local/share/locale\" -DPACKAGE_DATA_DIR=\"/usr/local/share/easytag\"    -g -O2 -Wall -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -MT mp4_header.o -MD -MP -MF ".deps/mp4_header.Tpo" -c -o mp4_header.o mp4_header.c; \        then mv -f ".deps/mp4_header.Tpo" ".deps/mp4_header.Po"; else rm -f ".deps/mp4_header.Tpo"; exit 1; fi
mp4_header.c:61: error: `MP4_MPEG4_AAC_HE_AUDIO_TYPE' undeclared here (not in a function)
mp4_header.c:61: error: initializer element is not constant
mp4_header.c:61: error: (near initialization for `MP4AudioProfileToName[4].profile')
mp4_header.c:61: error: initializer element is not constant
mp4_header.c:61: error: (near initialization for `MP4AudioProfileToName[4]')
mp4_header.c:62: error: initializer element is not constant
mp4_header.c:62: error: (near initialization for `MP4AudioProfileToName[5]')
mp4_header.c:63: error: initializer element is not constant
mp4_header.c:63: error: (near initialization for `MP4AudioProfileToName[6]')
mp4_header.c:64: error: initializer element is not constant
mp4_header.c:64: error: (near initialization for `MP4AudioProfileToName[7]')
mp4_header.c:65: error: initializer element is not constant
mp4_header.c:65: error: (near initialization for `MP4AudioProfileToName[8]')
mp4_header.c:67: error: initializer element is not constant
mp4_header.c:67: error: (near initialization for `MP4AudioProfileToName[9]')
mp4_header.c:68: error: initializer element is not constant
mp4_header.c:68: error: (near initialization for `MP4AudioProfileToName[10]')
mp4_header.c:69: error: initializer element is not constant
mp4_header.c:69: error: (near initialization for `MP4AudioProfileToName[11]')
mp4_header.c:70: error: initializer element is not constant
mp4_header.c:70: error: (near initialization for `MP4AudioProfileToName[12]')
mp4_header.c:71: error: initializer element is not constant
mp4_header.c:71: error: (near initialization for `MP4AudioProfileToName[13]')
mp4_header.c:72: error: initializer element is not constant
mp4_header.c:72: error: (near initialization for `MP4AudioProfileToName[14]')
mp4_header.c:74: error: initializer element is not constant
mp4_header.c:74: error: (near initialization for `MP4AudioProfileToName[15]')
mp4_header.c:75: error: initializer element is not constant
mp4_header.c:75: error: (near initialization for `MP4AudioProfileToName[16]')
mp4_header.c:76: error: initializer element is not constant
mp4_header.c:76: error: (near initialization for `MP4AudioProfileToName[17]')
mp4_header.c:77: error: initializer element is not constant
mp4_header.c:77: error: (near initialization for `MP4AudioProfileToName[18]')
mp4_header.c:78: error: initializer element is not constant
mp4_header.c:78: error: (near initialization for `MP4AudioProfileToName[19]')
mp4_header.c:79: error: initializer element is not constant
mp4_header.c:79: error: (near initialization for `MP4AudioProfileToName[20]')
mp4_header.c:80: error: initializer element is not constant
mp4_header.c:80: error: (near initialization for `MP4AudioProfileToName[21]')
mp4_header.c:81: error: initializer element is not constant
mp4_header.c:81: error: (near initialization for `MP4AudioProfileToName[22]')
mp4_header.c:82: error: initializer element is not constant
mp4_header.c:82: error: (near initialization for `MP4AudioProfileToName[23]')
mp4_header.c: In function `getType':
mp4_header.c:125: warning: implicit declaration of function `MP4GetTrackMediaDataName'
mp4_header.c:125: warning: initialization makes pointer from integer without a cast
mp4_header.c: In function `Mp4_Header_Read_File_Info':
mp4_header.c:240: warning: implicit declaration of function `MP4GetTrackAudioChannels'
make[3]: *** [mp4_header.o] Error 1
make[3]: Leaving directory `/usr/local/src/easytag/easytag-1.99.12/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/easytag/easytag-1.99.12/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/easytag/easytag-1.99.12'
make: *** [all] Error 2

```Any ideas why I would have an error?  Or why, for that matter it's not able to find the id3 library? (I installed id3lib, but it created libid3 apparently :-) )

---

### Post by Circus-Killer on 2007-01-15
just out of interest, why are you compiling it. why not just add universe and multiverse repositories and then just use apt-get to install easytag. the pre-compiled easytag packages for ubuntu already have mp3 support and works great.

---

### Post by mmcmonster on 2007-01-15
A couple reasons.  First, to understand the system a little better. :-)  Second, I believe the version in the Dapper repositories isn't the latest version.

---

### Post by mmcmonster on 2007-01-16
Bump. :-)

---

