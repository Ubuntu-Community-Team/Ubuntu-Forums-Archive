---
title: "avconv silently fails when input file count is over 50,000"
date: 2016-05-14
forum: Programming Talk
---

### Post by f00dl3 on 2016-05-14
I have a IP/USB webcam script that fetches images every 1.2 seconds on  average from 3 cameras, converts to a jpeg, then zips the jpegs up every 2 minutes (and generates a 64 color GIF for mobile viewing). This  works flawlessly. And since I'm using /dev/shm, it's not doing 250,000+ disk writes a day, saving my hard disk.  I have another script that kicks off at 3 AM to  unzip all the jpeg images to /dev/shm , then write them all to a mp4 file  with avconv.  When the image count was under 50,000 files, this worked  great as well. Now that the image count is over 50,000, it is failing (or only using 44 frames in this case),  without generating any error at all.
```

    EMail=""
    SourceFolder="/home/astump/Desktop/var/www/Get/Cams/Archive/"
    UnpackFolder="/dev/shm/mp4tmp"   I am stepping through each process to  show where it fails:

    mkdir -p $UnpackFolder
    # Works
    unzip  -j $SourceFolder/"*.zip" -d $UnpackFolder
    # 719 archives were successfully processed. Works - had to change  /dev/shm to 12 GB in /etc/fstab
    CamImgQty=$(ls -l  $UnpackFolder/*.jpeg | wc -l)
    # Returns 57623
    CamSizeSum=$(du  -c $UnpackFolder/*.jpeg | sed -n "\$s/\\t.*//p")
    # Returns 8565616
    bash /dev/shm/Sequence.sh $UnpackFolder/ jpeg
    # This script  renames all files to avconv's %05d format. File count remains 57623,  size remains 8565616.
    ls /dev/shm/mp4tmp/00*
    # says display all 999  possibilities. It works.
    avconv -threads 8 -framerate 24 -i  $UnpackFolder/%05d.jpeg -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" -vcodec  libx264 -pix_fmt yuv420p /var/www/Get/Cams/MP4/$(date -d "yesterday  12:00" +'%y%m%d').mp4
    # Fails.  Here is what avconv returns - does  not help at all!

ffmpeg version 2.8.6-1ubuntu2 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.3.1 (Ubuntu 5.3.1-11ubuntu1) 20160311
  configuration: --prefix=/usr --extra-version=1ubuntu2 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
[mjpeg @ 0x224e8a0] Changeing bps to 8
Input #0, image2, from '/dev/shm/mp4tmp/%05d.jpeg':
  Duration: 00:40:00.96, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: mjpeg, yuvj422p(pc, bt470bg/unknown/unknown), 1152x1006 [SAR 1:1 DAR 576:503], 24 fps, 24 tbr, 24 tbn, 24 tbc
[swscaler @ 0x22751e0] deprecated pixel format used, make sure you did set range correctly
[libx264 @ 0x225d320] using SAR=1/1
[libx264 @ 0x225d320] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX FMA3 AVX2 LZCNT BMI2
[libx264 @ 0x225d320] profile High, level 3.2
[libx264 @ 0x225d320] 264 - core 148 r2643 5c65704 - H.264/MPEG-4 AVC codec - Copyleft 2003-2015 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=12 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=24 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, mp4, to '/var/www/Get/Cams/MP4/160513.mp4':
  Metadata:
    encoder         : Lavf56.40.101
    Stream #0:0: Video: h264 (libx264) ([33][0][0][0] / 0x0021), yuv420p, 1152x1006 [SAR 1:1 DAR 576:503], q=-1--1, 24 fps, 12288 tbn, 24 tbc
    Metadata:
      encoder         : Lavc56.60.100 libx264
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg (native) -> h264 (libx264))
Press [q] to stop, [?] for help
frame=   44 fps=0.0 q=-1.0 Lsize=     118kB time=00:00:01.75 bitrate= 551.1kbits/s    
video:117kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.982486%
[libx264 @ 0x225d320] frame I:1     Avg QP:20.90  size: 24312
[libx264 @ 0x225d320] frame P:35    Avg QP:21.33  size:  2330
[libx264 @ 0x225d320] frame B:8     Avg QP:21.33  size:  1605
[libx264 @ 0x225d320] consecutive B-frames: 63.6% 36.4%  0.0%  0.0%
[libx264 @ 0x225d320] mb I  I16..4: 19.7% 72.6%  7.7%
[libx264 @ 0x225d320] mb P  I16..4:  1.4%  5.1%  0.1%  P16..4: 11.2%  0.9%  0.8%  0.0%  0.0%    skip:80.6%
[libx264 @ 0x225d320] mb B  I16..4:  0.3%  0.3%  0.0%  B16..8: 11.1%  0.5%  0.1%  direct: 2.2%  skip:85.5%  L0:50.0% L1:49.5% BI: 0.6%
[libx264 @ 0x225d320] 8x8 transform intra:76.1% inter:92.7%
[libx264 @ 0x225d320] coded y,uvDC,uvAC intra: 15.6% 15.7% 1.7% inter: 2.3% 2.8% 0.1%
[libx264 @ 0x225d320] i16 v,h,dc,p: 57% 25%  6% 11%
[libx264 @ 0x225d320] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 24%  6% 64%  1%  1%  1%  1%  1%  1%
[libx264 @ 0x225d320] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 32% 24% 15%  4%  5%  5%  5%  4%  5%
[libx264 @ 0x225d320] i8c dc,h,v,p: 83% 11%  6%  0%
[libx264 @ 0x225d320] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0x225d320] ref P L0: 53.3%  4.0% 27.5% 15.2%
[libx264 @ 0x225d320] ref B L0: 47.7% 52.3%
[libx264 @ 0x225d320] kb/s:517.97
```

---

### Post by wildmanne39 on 2016-05-14
*Thread moved to **Programming Talk**.*

---

### Post by f00dl3 on 2016-05-14
I developed a work-around and probably permanent solution to my issue. This is still a (bug?) - but to avoid this I am creating MP4 files instead of ZIP files every 2 minutes now, and simply concatenating the ~720 files at 3 AM instead of processing ~60,000 images. This is actually a lot less CPU and IO intensive. And it allows me to view images from cameras by 2 min increments without unzipping them.

---

### Post by mc4man on 2016-05-14
Whether it mattered or not no clue, just to mention - you are no longer using libav/avconv, it's been removed in favor of FFmpeg. So possibly commands/parameters may differ.
(- /usr/bin/avconv is now just a link to /usr/bin/ffmpeg

---

### Post by f00dl3 on 2016-05-14
Had nothing to do with file limits. My script is more efficient now with what I have done in this process of troubleshooting this, but the root cause was a few 0 byte jpegs mucking things up. Likely corrupt extractions from the ZIPs. Which is now avoided since I'm using MP4s.

---

