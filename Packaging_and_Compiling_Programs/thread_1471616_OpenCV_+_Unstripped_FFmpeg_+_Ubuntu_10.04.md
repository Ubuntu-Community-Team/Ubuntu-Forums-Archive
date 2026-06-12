---
title: "OpenCV + Unstripped FFmpeg + Ubuntu 10.04"
date: 2010-05-03
forum: Packaging and Compiling Programs
---

### Post by js911 on 2010-05-03
Hi all,

I'm trying to use OpenCV for video capture (and its other image processing features), but I get a steady stream of warnings from swscaler: "no accelerated colorspace conversion found". After a fair amount of research, it seems this is caused by using a "stripped" version of ffmpeg (LGPL instead of GPL). I am trying to follow the suggestion to recompile ffmpeg manually using this guide:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

The steps listed seem to work alright, though I apparently need to set --enable-shared as well. When I do this, I get errors asking me to recompile with -fPIC set. After some more research, it seems to have to do with shared libraries and 64 bit architectures. After building both x264 and ffmpeg with --enable-pic and --extra-cflags=-fPIC options, they both seem to work just fine.

However, I get the same compile error requesting I recompile with -fPIC when I try to make OpenCV. This time, however, there is no configure script where I can set this option. OpenCV is built using cmake. I'm stuck here, and I've been trying to get this working for the past 2 days. I would really appreciate if anyone could help!

Thanks

---

### Post by xzero1 on 2010-05-03
I suggest you post this in the "packaging and compiling" sub forum.

---

### Post by js911 on 2010-05-03
(This thread was posted in Multimedia forum but was suggested to move here)

Hi all,

I'm trying to use OpenCV for video capture (and its other image processing features), but I get a steady stream of warnings from swscaler: "no accelerated colorspace conversion found". After a fair amount of research, it seems this is caused by using a "stripped" version of ffmpeg (LGPL instead of GPL). I am trying to follow the suggestion to recompile ffmpeg manually using this guide:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

The steps listed seem to work alright, though I apparently need to set --enable-shared as well. When I do this, I get errors asking me to recompile with -fPIC set. After some more research, it seems to have to do with shared libraries and 64 bit architectures. After building both x264 and ffmpeg with --enable-pic and --extra-cflags=-fPIC options, they both seem to work just fine.

However, I get the same compile error requesting I recompile with -fPIC when I try to make OpenCV. This time, however, there is no configure script where I can set this option. OpenCV is built using cmake. I'm stuck here, and I've been trying to get this working for the past 2 days. I would really appreciate if anyone could help!

Thanks

---

### Post by FakeOutdoorsman on 2010-05-04
I'm not sure what OpenCV is or does, but I got it to compile:

1. Follow the [how to compile FFmpeg](http://ubuntuforums.org/showthread.php?t=786095) guide you linked to, except add *--enable-shared* during the x264 and FFmpeg *./configure* steps.  Once you install FFmpeg, run *sudo ldconfig*.  I doubt you need to add any *--extra-cflags*.  I believe *--enable-shared* automatically implies *--enable-pic* on x86_64.

2. Get some OpenCV dependencies:
```
sudo apt-get install build-essential cmake pkg-config
```
You will have already installed build-essential if you followed the FFmpeg guide.

3. Get OpenCV source and compile.  I didn't know if you tried to install the stable version or SVN, so I chose SVN:
```
cd
svn co https://code.ros.org/svn/opencv/trunk
cd opencv
mkdir release
cd release
cmake ../ -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=/usr/local
make
sudo checkinstall --pkgname opencv-svn --pkgversion 3050 --default --backup=no
```

Not sure if it actually works though.  Since you already installed x264 and FFmpeg, I would follow the **Updating Your Installation** section of the FFmpeg guide before you attempt to compile OpenCV.

---

### Post by lisati on 2010-05-04
Threads merged. 
(It's ok to use the "Report Abuse" button [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] to ask a staff member to move the thread.)

---

### Post by js911 on 2010-05-05
Thanks for the help, FakeOutdoorsman, and for moving the thread, lisati.

Using --enable-shared (ffmpeg) and --enable-pic (x264) with ldconfig after making worked for me, thanks a lot! I *think* I needed to use the pic flag on x264 (not shared) to get it to work, though I got it working just before you posted so I didn't test your solution. Either way, I'm grateful for the assistance. I'm relatively new to Linux, so shared libraries and position independent code are new concepts to me.

---

### Post by charliep84 on 2010-10-05
Hi,
I need your help please. I am in exactly the same situation as js911 (ubuntu 10.04, 64 bit, want to use opencv,  warnings from swscaler), but unfortunately the guide given by you on this site does not work for me:
=> I tried --enable-shared and --enable-pic for both ffmpeg and x264 and I was following this guide ([http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)), but I always get stuck when I try to make ffmpeg. (js911's proposition did not work either). The following message appears in the terminal:

/usr/bin/ld: /usr/local/lib/libvpx.a(vpx_codec.c.o): relocation R_X86_64_32 against `,ridata,str1,1' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libvpx.a:could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libavcodec/libavcodec.so52] Error 1

I would be very grateful if you helped me! Thank you very much!

---

### Post by mngcld on 2010-11-06
> **charliep84 said:**
> 
/usr/bin/ld: /usr/local/lib/libvpx.a(vpx_codec.c.o): relocation R_X86_64_32 against `,ridata,str1,1' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libvpx.a:could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [libavcodec/libavcodec.so52] Error 1

I think you should include --enable-livpx when compiling ffmpeg.

Anyway I am not able to solve the main problem. OpenCv compiles, but I continue getting messages like 
```

[swscaler @ 0x1666620]No accelerated colorspace conversion found.

```
when I try to run a video with play.c (attached as play.doc, just rename it and compile with 
```

gcc `pkg-config --cflags opencv --libs opencv` -o play ./play.c

```
).

I run update_open_cv.sh (attached) to compile ffmpeg, x264 and opencv. I also tried to put both --enable-shared and --enable-pic in the options of ./configure for ffmpeg and x264, but I get the same error message when running the program attached.

I am using ubuntu 10.04 on a 64 bit machine. I don't think 64 bit is the main problem, I installed a 32 bit version of ubuntu on the same machine and there is always the same message at runtime.

The other script, install_opencv.sh, should be used for a fresh install. I found it somewhere on internet and it repeats more or less what is in the post about compiling ffmpeg and x264.

Please help!! I need to make it work!!

---

### Post by mngcld on 2010-11-08
Hallo again! I solved this problem, in the sense that now the message about the colorspace conversion doesn't appear anymore. Anyway the program play.c is not working as it should, the trackbar doesn't move correctly. Maybe they changed something in opencv and one should write it in some other way.. 

Regarding the compilation I use --enable-shared and --enable-pic in the configure for x264 and --enable-shared for ffmpeg. I also had that problem with livpx and you can put --enable-libvpx, but it works just with the precompiled package, not if you compile it before ffmpeg as in the other post before ffmpeg.

Hope it can help!

---

### Post by pvfloripa on 2011-03-02
Thanks guys! I use OpenCV and this swscaler message had been annoying me for several months. For me, it worked to recompile ffmpeg with --enable-shared and x264 with --enable-shared and --enable-pic, followed by ldconfig.

---

### Post by hus787 on 2011-10-30
> **pvfloripa said:**
> Thanks guys! I use OpenCV and this swscaler message had been annoying me for several months. For me, it worked to recompile ffmpeg with --enable-shared and x264 with --enable-shared and --enable-pic, followed by ldconfig.
 
please help me out! i can't figure out what to do with this[COLOR=#BE1414][FONT=Monospace]"[swscaler @ 0x7f42001f81e0]No accelerated colorspace conversion found from yuv420p to bgr24."[/FONT][/COLOR] error when i do cvqueryframe(CvCapture** capture).

im working on a opencv project with qt libraries.

its not been 1 week since i have switched to linux after saying my farewell to windows7

this error never occurred in windows7

ive spent like 3 days googling, reading and implementing suggestions from [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) etc and the 1s on this thread itself but to no avail.i even tried wat u did but still the same.

when i try to sudo make install after -enable-shared and make i get the same error as charliep84 stated. i tried enable-libvpx but got an error saying "ERROR: libvpx decoder version must be >=0.9.1"

please help me out with the steps i should be following. keep in mind im a newbie and don't know almost anything linux.

---

### Post by hus787 on 2011-11-03
problem solved. [http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/](http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/)

---

