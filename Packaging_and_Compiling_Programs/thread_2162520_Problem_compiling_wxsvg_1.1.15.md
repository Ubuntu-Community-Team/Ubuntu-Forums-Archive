---
title: "Problem compiling wxsvg 1.1.15"
date: 2013-07-14
forum: Packaging and Compiling Programs
---

### Post by Botruckle on 2013-07-14
I downloaded the bz2 source and unpacked it and got most of the way through make, but then got this error about 'AVStream' has no member named 'r_frame_rate':

```

libtool: compile:  g++ -DPACKAGE_NAME=\"wxsvg\" -DPACKAGE_TARNAME=\"wxsvg\" -DPACKAGE_VERSION=\"1.1.15\" "-DPACKAGE_STRING=\"wxsvg 1.1.15\"" -DPACKAGE_BUGREPORT=\"wx-svg-users@lists.sourceforge.net\" -DPACKAGE_URL=\"\" -DPACKAGE=\"wxsvg\" -DVERSION=\"1.1.15\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DHAVE_LIBEXPAT=1 -I. -I../include -I../include/wxSVG -g -O2 -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -DUSE_RENDER_CAIRO -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread -DUSE_LIBAV -I/usr/local/include -MT mediadec_ffmpeg.lo -MD -MP -MF .deps/mediadec_ffmpeg.Tpo -c mediadec_ffmpeg.cpp  -fPIC -DPIC -o .libs/mediadec_ffmpeg.o
mediadec_ffmpeg.cpp: In member function 'virtual float wxFfmpegMediaDecoder::GetFps()':
mediadec_ffmpeg.cpp:111:58: error: 'AVStream' has no member named 'r_frame_rate'
mediadec_ffmpeg.cpp:111:82: error: 'AVStream' has no member named 'r_frame_rate'
mediadec_ffmpeg.cpp:112:26: error: 'AVStream' has no member named 'r_frame_rate'
mediadec_ffmpeg.cpp:112:50: error: 'AVStream' has no member named 'r_frame_rate'
make[2]: *** [mediadec_ffmpeg.lo] Error 1
make[2]: Leaving directory `/home/jw/Downloads/DVDStyler/version_2.5/wxsvg-1.1.15/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jw/Downloads/DVDStyler/version_2.5/wxsvg-1.1.15/src'
make: *** [all-recursive] Error 1
jw@JW-PC:~/Downloads/DVDStyler/version_2.5/wxsvg-1.1.15$

```

I'm doing this compile before compiling the latest DVDStyler (2.5) on Ubuntu 13.04. The error mentions ffmpeg, but that program has been working fine. I have DVDStyler 2.1 installed currently. (Version 2.3.4 doesn't work, won't create ISOs, so I've been using 2.1)

If it helps, here is my ffmpeg info:

```

ffmpeg version git-2013-02-18-c63f9fb Copyright (c) 2000-2013 the FFmpeg developers
  built on Feb 17 2013 22:58:27 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3 --enable-pthreads --enable-libopus
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100

```

Thanks for any insights!

---

### Post by mc4man on 2013-07-15
I gave a quick try on 1.1.15 using 2 different ffmpeg source build I have installed here, one slightly older than your's  - 1.0.6,  & today's latest git.

In both cases 1.1.15 built fine. 
So maybe your ffmpeg is somehow incompatible

Your could try updating your ffmpeg or maybe try the libav that's in 13.04 (it's a bit old but may work.
If you try the system libav then you better remove your static ffmpeg build first or it may get used no matter what you do
(can be re-installed after your build of 1.1.15, ect.

If wanting to use FFmpeg git & on a 64 bit install then it's quite possible the 1.1.15 build will fail at the end, in that case you'll need to either fix the rodata error or build FFmpeg as shared which may require a different strategy
( in that case I'd build the whole deal to a dir. in /opt & link dvdstyler at runtime if needed

---

### Post by Botruckle on 2013-07-17
Thanks, I'll give that a try.

---

### Post by Ubunterrific on 2013-07-30
> **Botruckle said:**
> Thanks, I'll give that a try.

How'd it go? All good?

---

### Post by Botruckle on 2013-08-06
First I tried doing a reinstall of ffmpeg and its dependencies (using git from the Ubuntu Compilation Guide for ffmpeg), but I still get the error when compiling wxsvg. I haven't yet tried building to a different location.

---

