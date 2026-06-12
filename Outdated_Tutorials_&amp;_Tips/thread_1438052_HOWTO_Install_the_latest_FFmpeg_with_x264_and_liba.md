---
title: "HOWTO: Install the latest FFmpeg with x264 and libavfilter"
date: 2010-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by BrandonMintern on 2010-03-24
These instructions are for Ubuntu Karmic Koala 9.10. Most of the details for this guide are covered in [_**HOWTO: Install and use the latest FFmpeg and x264**_]("http://ubuntuforums.org/showthread.php?t=786095"). This guide is intended to quickly get you up and running with libavfilter once you are familiar with the linked HOWTO. For that reason, this guide will be as minimal as possible.

_**Initial Installation**_
1. Uninstall blockers
```
sudo apt-get remove ffmpeg x264 libx264-dev
```
2. Install dependencies
```
sudo apt-get update
sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libx11-dev libxfixes-dev libxvidcore4-dev zlib1g-dev
```
3. Create and cd to the directory you would like your source files to live in. In my case it will be ~/ffmpeg-x264-avfilter
```
cd
mkdir ffmpeg-x264-avfilter
cd ffmpeg-x264-avfilter
```
4. Install x264 from latest sources
```
git clone git://git.videolan.org/x264.git
cd x264
./configure
make
sudo checkinstall --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`+`git rev-list HEAD -n 1 | head -c 7`" --backup=no --default
```
(Note that I'm skipping the libtheora step from the above-linked guide. If you need it, make sure to refer to that guide.)
5. Fetch libavfilter and ffmpeg sources
```
cd ..
svn checkout svn://svn.ffmpeg.org/soc/libavfilter
cd libavfilter
./checkout.sh
```
6. Make and install ffmpeg with libavfilter
```
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libxvid --enable-x11grab --enable-avfilter --enable-avfilter-lavf
make
sudo checkinstall --pkgname=ffmpeg-avfilter --pkgversion "4:0.5+svn`date +%Y%m%d`" --backup=no --default
```
7. Verify your installation
```
hash ffmpeg
ffmpeg -filters
```


_**Updating to latest libavfilter**_ Not now! Only perform this when necessary.
```
sudo apt-get remove ffmpeg-avfilter
cd ~/ffmpeg-x264-avfilter/
svn checkout svn://svn.ffmpeg.org/soc/libavfilter
cd libavfilter
sudo rm -rf ffmpeg
./checkout.sh
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libxvid --enable-x11grab --enable-avfilter --enable-avfilter-lavf
make
sudo checkinstall --pkgname=ffmpeg-avfilter --pkgversion "4:0.5+svn`date +%Y%m%d`" --backup=no --default
```

**_Useful Note_**: It is pretty difficult to find useful documentation for libavfilter online. Point your browser at ~/ffmpeg-x264-avfilter/libavfilter/ffmpeg/doc/libavfilter.html (if you named your source directory as I did) for the full documentation on your version of libavfilter.

**_Another Note_**: libavfilter seems to be pretty unstable right now. If you'd like to try to debug a crash, invoke ffmpeg by using ~/ffmpeg-x264-avfilter/libavfilter/ffmpeg/ffmpeg_g as the command. This is the non-stripped version of ffmpeg. Alternatively you could pass --disable-stripping to the ffmpeg ./configure command (I think).

**_Disclaimer_**: This works for me with libavfilter revision 5715 -- the checkout.sh script should automatically pull in the appropriate ffmpeg version. It is possible that I have made a mistake or a typo in this guide, as I threw it together pretty quickly after I got it to work for me. Let me know any errors I may have made and I'll be happy to correct them.

---

### Post by andrew.46 on 2010-07-24
Hi Brandon,

I have only just started to have a look at libavfilter, but it seems this has been integrated with the svn FFmpeg code now? Or at least major portions of this work...

Andrew

---

### Post by BrandonMintern on 2010-07-24
Hi! I'm not exactly sure, I haven't used it in a while. One issue is that if it is integrated, it might not be the latest libavfilter. I know that just a couple months ago, I had a fade filter integrated into libavfilter, and I have no idea if that is yet in ffmpeg.

---

### Post by andrew.46 on 2010-07-24
Hi Brandon,

> **BrandonMintern said:**
> Hi! I'm not exactly sure, I haven't used it in a while. One issue is that if it is integrated, it might not be the latest libavfilter. I know that just a couple months ago, I had a fade filter integrated into libavfilter, and I have no idea if that is yet in ffmpeg.

Good point, the integration is described as a 'work in progress' in the docs. A default install has only the following atm:

```

andrew@skamandros~$ ffmpeg -filters
FFmpeg version SVN-r24430, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 22 2010 23:14:54 with gcc 4.4.4
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static 
--disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab
 --enable-libmp3lame --enable-libx264 --enable-libfaac
 --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 
--enable-zlib --enable-libvpx --enable-libgsm --enable-nonfree 
--enable-gpl
  libavutil     50.22. 0 / 50.22. 0
  libavcore      0. 0. 0 /  0. 0. 0
  libavcodec    52.84. 0 / 52.84. 0
  libavformat   52.76. 0 / 52.76. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.26. 1 /  1.26. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Filters:
aspect           Set the frame aspect ratio.
crop             Crop the input video to x:y:width:height.
format           Convert the input video to one of the specified pixel formats.
noformat         Force libavfilter not to use any of the specified pixel formats for the input to the next filter.
null             Pass the source unchanged to the output.
pad              Pad input image to width:height[:x:y[:color]] (default x and y: 0, default color: black).
pixdesctest      Test pixel format definitions.
pixelaspect      Set the pixel aspect ratio.
scale            Scale the input video to width:height size and/or convert the image format.
slicify          Pass the images of input video on to next video filter as multiple slices.
unsharp          Sharpen or blur the input video.
vflip            Flip the input video vertically.
buffer           Buffer video frames, and make them accessible to the filterchain.
color            Provide an uniformly colored input, syntax is: [color[:size[:rate]]]
nullsrc          Null video source, never return images.
nullsink         Do absolutely nothing with the input video.


```

I am not entirely clear what the option:

```
  --enable-avfilter-lavf   video filters dependent on avformat [no]
```

adds to the mix but I shall enable it with the next update just for curiosity. 

Andrew

---

