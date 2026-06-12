---
title: "Compiling C code for FFmpeg on Ubuntu"
date: 2013-09-24
forum: Packaging and Compiling Programs
---

### Post by Koustubh on 2013-09-24
Hi,

I am new to using gcc. I have FFmpeg installed on Ubuntu 12.04 LTS. I am trying to write a C code for transcoding using the FFmpeg libraries. The details are as below:

I have all the necessary libraries in the directory : /home/ffmpeg/ffmpeg_sources. Also, my program videoEncoding.c (which at the moment does nothing, just trying to compile) is in the same directory

ffmpeg@ubuntu:~/ffmpeg_sources$ pwd
/home/ffmpeg/ffmpeg_sources

ffmpeg@ubuntu:~/ffmpeg_sources$ ls
fdk-aac      lame-3.99.5.tar.gz  opus-1.0.3.tar.gz  yasm-1.2.0
ffmpeg       libvpx              videoEncoding.c    yasm-1.2.0.tar.gz
lame-3.99.5  opus-1.0.3          x264


ffmpeg@ubuntu:~/ffmpeg_sources/ffmpeg$ pwd
/home/ffmpeg/ffmpeg_sources/ffmpeg
ffmpeg@ubuntu:~/ffmpeg_sources/ffmpeg$ ls
1                       COPYING.LGPLv2.1  libavcodec     Makefile
a.out                   COPYING.LGPLv3    libavdevice    presets
arch.mak                CREDITS           libavfilter    README
Changelog               doc               libavformat    RELEASE
cmdutils.c              ffmpeg.c          libavresample  test.c
cmdutils_common_opts.h  ffmpeg_filter.c   libavutil      tests
cmdutils.h              ffmpeg.h          libpostproc    tools
common.mak              ffmpeg_opt.c      library.mak    version.sh
compat                  ffplay.c          libswresample  videoEncoding.c
configure               ffprobe.c         libswscale
COPYING.GPLv2           ffserver.c        LICENSE
COPYING.GPLv3           INSTALL           MAINTAINERS
ffmpeg@ubuntu:~/ffmpeg_sources/ffmpeg$ 



videoEncoding.c is as follows:

ffmpeg@ubuntu:~/ffmpeg_sources$ cat videoEncoding.c 
#include "ffmpeg/libavcodec/avcodec.h"
#include "ffmpeg/libavformat/avformat.h"
int main(int argc, charg *argv[]) {
}

When I compile this, I get the following:

ffmpeg@ubuntu:~/ffmpeg_sources$ gcc videoEncoding.c 
In file included from videoEncoding.c:1:0:
ffmpeg/libavcodec/avcodec.h:31:33: fatal error: libavutil/samplefmt.h: No such file or directory
compilation terminated.

Now, I understand this is just a matter of placing the code in the right directory. As seen from the previous output, the libraries are all present. Could someone please help me compile this?

---

### Post by oldos2er on 2013-09-24
Moved to Packaging & Compiling Programs, because compiling code is not generally an 'Absolute Beginner' task.

---

### Post by lukeiamyourfather on 2013-09-24
Have you seen this guide?

[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Also ffmpeg is a rolling release so a bug you encounter today might not be there tomorrow.

---

### Post by Koustubh on 2013-09-24
Yes, I followed this very guide and I was able to successfully install it. The problem comes when I write my own code and try to compile it.

---

### Post by FakeOutdoorsman on 2013-10-01
Try the [libav-user mailing list](http://ffmpeg.org/mailman/admindb/libav-user) which is the list for using the FFmpeg libraries.

---

