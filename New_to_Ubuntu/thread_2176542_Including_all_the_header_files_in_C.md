---
title: "Including all the header files in C"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by Koustubh on 2013-09-24
HI,

I am new to gcc and I was wondering if I could include all the header files present in a library in a C program. It may not be a good practice, but I would like to do it.

koustubh

---

### Post by Impavidus on 2013-09-25
No, not really good practice. Sometimes it may even lead to problems. Execute in the directory with your source code```

echo "/* These are all header files */" >allheaders.h
for file in /usr/include/*.h
do
echo "#include <${file:13}>" >>allheaders.h
done

```
and write at the top of your code```

#include "allheaders.h"
```
This will include every header from /usr/include.

---

### Post by col48 on 2013-09-25
In my experience, it is best to try to adopt good practice right from the start - it's harder and less satisfying to try to sort out issues later which are due to bad habits.  It may cost a bit of time to start with but it pays off in the end.  If someone is advocating a particular habit as "good practice", it's a good idea to ask yourself why; if it really **_is_** good practice, it will help you to produce code which is easier to debug and understand and which you can come back to in a couple of years without embarrassment.

Part of the point of OO is to keep each unit of code small and with one purpose.  By including loads of unused headers you risk confusing yourself and reduce the chance of really getting to know what goes with what (and perhaps the oddities which come with using anything coded by someone else!).

I hope you are able to get out of C/C++ all that you want and need to enjoy working with it.

---

### Post by Impavidus on 2013-09-25
Oh, yes, I fully agree with that. It's really bad practice. On the other hand, this won't turn the OP's machine into a spam bot and the best way to learn is sometimes from your own mistakes.

---

### Post by Koustubh on 2013-09-25
Hi,
Thanks for the reply guys. I understand its not a good practice. So can any one pls help me out here?

I have FFmpeg installed on Ubuntu 12.04 LTS. I am trying to write a C  code for transcoding using the FFmpeg libraries. The details are as  below:

I have all the necessary libraries in the directory :  /home/ffmpeg/ffmpeg_sources. Also, my program videoEncoding.c (which at  the moment does nothing, just trying to compile) is in the same  directory

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

Now, I understand this is just a matter of placing the code in the right  directory. As seen from the previous output, the libraries are all  present. Could someone please help me compile this?

---

### Post by Impavidus on 2013-09-25
I see.

The dirty solution is to include the local directory in the search path for header files included with #include <file.h>. Use gcc with the -I<dir> option. I see you have the source code of a library. Make sure you have compiled it before you can link your program to it.

The nice solution is to install your library the ordinary way. Install the packages **libavutil-dev**, **libavcodec-dev**, **libavdevice-dev** etc. with the package manager (apt-get, software centre, whatever you like). Most depend on each other, so installing one or two will pull in the rest as dependencies. This should put the compiled libraries and the header files in the standard directories, where gcc can find them without you specifying where to look for them. You only need to use **#include <libavcodec/avcodec.h>** etc. in your program.

---

