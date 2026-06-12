---
title: "FFMPEG: Converting for youtube gray screen problem"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2013-02-25
I recorded my screen using ffmpeg and converted from mkv to mp4 and uploaded to youtube. But all I see on the video is gray nothing else. The audio still plays though, I tried converting to numerous formats but no luck.

Here the code for recording the desktop (If it helps)
```

ffmpeg -f x11grab -r 25 -s 1366x768 -i :0.0 -f alsa -ac 2 -i pulse -vcodec libx264 -preset ultrafast -crf 0 video.mkv

```How I tried converting:
```

ffmpeg -i foo.mkv bar.mp4

```I also tried using parameter *-vcodec* but no luck.

Thanks In Advance

---

### Post by FakeOutdoorsman on 2013-02-25
Did you upload "video.mkv" or "bar.mp4"? It is unclear what video you uploaded. Also, include your complete ffmpeg console output for each command. I have an idea of what the issue is, but it is only a guess without the ffmpeg console outputs.

---

### Post by scratman on 2013-02-25
Hey FakeOutdoorsman, long time no see.

WinFF is in the Software Centre, it provides a GUI for WinFF and takes care of all of the terminal commands for you.  It can insure you against typos that can be difficult to spot.

hth

---

### Post by cyb3r_sn4k3 on 2013-02-26
> **FakeOutdoorsman said:**
> Did you upload "video.mkv" or "bar.mp4"? It is unclear what video you uploaded. Also, include your complete ffmpeg console output for each command. I have an idea of what the issue is, but it is only a guess without the ffmpeg console outputs.


Sorry about that, I tried uploading both video.mkv and bar.mp4
I dont think I have the outputs with me now. Ill try to simulate what I did before but before that is there specific arguments I should use in ffmpeg for uploading video to youtube ?

---

### Post by cyb3r_sn4k3 on 2013-02-26
Output for ffmpeg -i hope.mkv test.mp4
```

ffmpeg -i hope.mkv test.mp4
ffmpeg version git-2013-01-20-b3b456b Copyright (c) 2000-2013 the FFmpeg developers
  built on Jan 20 2013 10:38:32 with gcc 4.7 (Ubuntu/Linaro 4.7.2-2ubuntu1)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 15.100 / 52. 15.100
  libavcodec     54. 89.100 / 54. 89.100
  libavformat    54. 61.101 / 54. 61.101
  libavdevice    54.  3.102 / 54.  3.102
  libavfilter     3. 32.101 /  3. 32.101
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
Input #0, matroska,webm, from 'hope.mkv':
  Metadata:
    title           : Plc.4 Mie Haed
    MAJOR_BRAND     : isom
    MINOR_VERSION   : 512
    COMPATIBLE_BRANDS: isomiso2avc1mp41
    ARTIST          : Linkin Park
    ALBUM           : Reanimation
    DATE            : 2002
    track           : 7
    GENRE           : Rock
    ENCODER         : Lavf54.61.101
  Duration: 00:03:09.08, start: 0.000000, bitrate: 375 kb/s
    Stream #0:0(und): Video: h264 (High 4:4:4 Predictive), yuv444p, 1366x768, SAR 1:1 DAR 683:384, 25 fps, 25 tbr, 1k tbn, 50 tbc (default)
    Metadata:
      LANGUAGE        : und
      HANDLER_NAME    : VideoHandler
    Stream #0:1(und): Audio: vorbis, 44100 Hz, stereo, fltp (default)
    Metadata:
      LANGUAGE        : und
      HANDLER_NAME    : SoundHandler
[libx264 @ 0xaa1b720] using SAR=1/1
[libx264 @ 0xaa1b720] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.1 Cache64
[libx264 @ 0xaa1b720] profile High 4:4:4 Predictive, level 3.2, 4:4:4 8-bit
[libx264 @ 0xaa1b720] 264 - core 129 r2 bc13772 - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=4 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, mp4, to 'test.mp4':
  Metadata:
    title           : Plc.4 Mie Haed
    MAJOR_BRAND     : isom
    MINOR_VERSION   : 512
    COMPATIBLE_BRANDS: isomiso2avc1mp41
    ARTIST          : Linkin Park
    ALBUM           : Reanimation
    DATE            : 2002
    track           : 7
    GENRE           : Rock
    encoder         : Lavf54.61.101
    Stream #0:0(und): Video: h264 ([33][0][0][0] / 0x0021), yuv444p, 1366x768 [SAR 1:1 DAR 683:384], q=-1--1, 12800 tbn, 25 tbc (default)
    Metadata:
      LANGUAGE        : und
      HANDLER_NAME    : VideoHandler
    Stream #0:1(und): Audio: aac ([64][0][0][0] / 0x0040), 44100 Hz, stereo, s16, 128 kb/s (default)
    Metadata:
      LANGUAGE        : und
      HANDLER_NAME    : SoundHandler
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libx264)
  Stream #0:1 -> #0:1 (vorbis -> libfaac)
Press [q] to stop, [?] for help
frame=   44 fps=0.0 q=0.0 size=       0kB time=00:00:01.68 bitrate=   0.2kbits/sframe=   54 fps= 54 q=28.0 size=     159kB time=00:00:02.12 bitrate= 609.9kbits/frame=   70 fps= 45 q=28.0 size=     169kB time=00:00:02.75 bitrate= 501.9kbits/frame=   87 fps= 42 q=28.0 size=     182kB time=00:00:03.43 bitrate= 435.4kbits/frame=  107 fps= 42 q=25.0 size=     212kB time=00:00:04.24 bitrate= 409.2kbits/frame=  119 fps= 39 q=28.0 size=     429kB time=00:00:04.73 bitrate= 743.4kbits/frame=  137 fps= 38 q=28.0 size=     575kB time=00:00:05.45 bitrate= 864.9kbits/frame=  156 fps= 38 q=28.0 size=     616kB time=00:00:06.19 bitrate= 815.2kbits/frame=  176 fps= 37 q=28.0 size=     782kB time=00:00:07.00 bitrate= 914.8kbits/frame=  198 fps= 38 q=28.0 size=     802kB time=00:00:07.88 bitrate= 832.8kbits/frame=  218 fps= 38 q=28.0 size=     843kB time=00:00:08.67 bitrate= 795.5kbits/frame=  234 fps= 37 q=28.0 size=     906kB time=00:00:09.32 bitrate= 795.6kbits/frame=  252 fps= 37 q=28.0 size=     928kB time=00:00:10.04 bitrate= 757.0kbits/frame=  271 fps= 37 q=28.0 size=     947kB time=00:00:10.79 bitrate= 719.2kbits/frame=  289 fps= 37 q=28.0 size=     964kB time=00:00:11.51 bitrate= 686.1kbits/frame=  308 fps= 37 q=28.0 size=     982kB time=00:00:12.27 bitrate= 655.1kbits/frame=  327 fps= 37 q=28.0 size=    1004kB time=00:00:13.06 bitrate= 629.5kbits/frame=  345 fps= 37 q=28.0 size=    1016kB time=00:00:13.76 bitrate= 604.8kbits/frame=  364 fps= 37 q=28.0 size=    1033kB time=00:00:14.52 bitrate= 582.3kbits/frame=  383 fps= 37 q=28.0 size=    1050kB time=00:00:15.29 bitrate= 562.2kbits/frame=  400 fps= 37 q=28.0 size=    1065kB time=00:00:15.99 bitrate= 545.7kbits/frame=  420 fps= 37 q=28.0 size=    1082kB time=00:00:16.78 bitrate= 528.4kbits/frame=  437 fps= 37 q=28.0 size=    1279kB time=00:00:17.45 bitrate= 600.4kbits/frame=  455 fps= 36 q=28.0 size=    1295kB time=00:00:18.17 bitrate= 583.6kbits/frame=  472 fps= 36 q=28.0 size=    1310kB time=00:00:18.87 bitrate= 568.6kbits/frame=  492 fps= 36 q=28.0 size=    1327kB time=00:00:19.63 bitrate= 553.6kbits/frame=  513 fps= 37 q=28.0 size=    1344kB time=00:00:20.49 bitrate= 537.3kbits/frame=  533 fps= 37 q=28.0 size=    1357kB time=00:00:21.28 bitrate= 522.4kbits/frame=  553 fps= 37 q=28.0 size=    1373kB time=00:00:22.09 bitrate= 509.1kbits/frame=  570 fps= 37 q=28.0 size=    1388kB time=00:00:22.77 bitrate= 499.5kbits/frame=  587 fps= 37 q=28.0 size=    1403kB time=00:00:23.44 bitrate= 490.1kbits/frame=  602 fps= 36 q=28.0 size=    1413kB time=00:00:24.04 bitrate= 481.2kbits/frame=  619 fps= 36 q=28.0 size=    1426kB time=00:00:24.72 bitrate= 472.4kbits/frame=  634 fps= 36 q=28.0 size=    1439kB time=00:00:25.32 bitrate= 465.3kbits/frame=  651 fps= 36 q=28.0 size=    1454kB time=00:00:25.99 bitrate= 458.1kbits/frame=  671 fps= 36 q=28.0 size=    1467kB time=00:00:26.81 bitrate= 448.1kbits/frame=  686 fps= 36 q=28.0 size=    1662kB time=00:00:27.39 bitrate= 497.1kbits/frame=  701 fps= 36 q=28.0 size=    1676kB time=00:00:27.99 bitrate= 490.4kbits/frame=  718 fps= 36 q=28.0 size=    1689kB time=00:00:28.69 bitrate= 482.3kbits/frame=  735 fps= 36 q=28.0 size=    1702kB time=00:00:29.36 bitrate= 474.8kbits/frame=  752 fps= 36 q=28.0 size=    1716kB time=00:00:30.01 bitrate= 468.3kbits/frame=  774 fps= 36 q=28.0 size=    1740kB time=00:00:30.92 bitrate= 461.0kbits/frame=  797 fps= 36 q=28.0 size=    1757kB time=00:00:31.82 bitrate= 452.2kbits/frame=  816 fps= 36 q=28.0 size=    1770kB time=00:00:32.61 bitrate= 444.6kbits/frame=  833 fps= 36 q=28.0 size=    1786kB time=00:00:33.29 bitrate= 439.5kbits/frame=  854 fps= 36 q=28.0 size=    1804kB time=00:00:34.12 bitrate= 433.1kbits/frame=  869 fps= 36 q=28.0 size=    1815kB time=00:00:34.73 bitrate= 428.1kbits/frame=  882 fps= 36 q=28.0 size=    1827kB time=00:00:35.24 bitrate= 424.7kbits/frame=  895 fps= 35 q=28.0 size=    1837kB time=00:00:35.75 bitrate= 421.0kbits/frame=  911 fps= 35 q=28.0 size=    1851kB time=00:00:36.40 bitrate= 416.5kbits/frame=  926 fps= 35 q=28.0 size=    2048kB time=00:00:36.98 bitrate= 453.7kbits/frame=  941 fps= 35 q=28.0 size=    2062kB time=00:00:37.60 bitrate= 449.1kbits/frame=  955 fps= 35 q=28.0 size=    2075kB time=00:00:38.16 bitrate= 445.3kbits/frame=  970 fps= 34 q=28.0 size=    2087kB time=00:00:38.77 bitrate= 440.9kbits/frame=  987 fps= 34 q=28.0 size=    2103kB time=00:00:39.44 bitrate= 436.7kbits/frame= 1003 fps= 34 q=28.0 size=    2117kB time=00:00:40.09 bitrate= 432.5kbits/frame= 1019 fps= 34 q=28.0 size=    2131kB time=00:00:40.72 bitrate= 428.7kbits/frame= 1035 fps= 34 q=28.0 size=    2142kB time=00:00:41.34 bitrate= 424.4kbits/frame= 1055 fps= 34 q=28.0 size=    2158kB time=00:00:42.16 bitrate= 419.2kbits/frame= 1079 fps= 34 q=28.0 size=    2177kB time=00:00:43.11 bitrate= 413.7kbits/frame= 1103 fps= 35 q=28.0 size=    2196kB time=00:00:44.08 bitrate= 408.1kbits/frame= 1123 fps= 35 q=28.0 size=    2213kB time=00:00:44.87 bitrate= 404.0kbits/frame= 1145 fps= 35 q=28.0 size=    2233kB time=00:00:45.78 bitrate= 399.5kbits/frame= 1167 fps= 35 q=28.0 size=    2249kB time=00:00:46.64 bitrate= 394.9kbits/frame= 1184 fps= 35 q=28.0 size=    2447kB time=00:00:47.33 bitrate= 423.5kbits/frame= 1208 fps= 35 q=28.0 size=    2467kB time=00:00:48.29 bitrate= 418.4kbits/frame= 1227 fps= 35 q=28.0 size=    2483kB time=00:00:49.03 bitrate= 414.8kbits/frame= 1250 fps= 35 q=28.0 size=    2501kB time=00:00:49.93 bitrate= 410.3kbits/frame= 1272 fps= 35 q=28.0 size=    2518kB time=00:00:50.82 bitrate= 405.8kbits/frame= 1294 fps= 36 q=28.0 size=    2535kB time=00:00:51.72 bitrate= 401.5kbits/frame= 1318 fps= 36 q=28.0 size=    2555kB time=00:00:52.67 bitrate= 397.3kbits/frame= 1340 fps= 36 q=28.0 size=    2572kB time=00:00:53.53 bitrate= 393.5kbits/frame= 1362 fps= 36 q=28.0 size=    2588kB time=00:00:54.44 bitrate= 389.3kbits/frame= 1385 fps= 36 q=28.0 size=    2606kB time=00:00:55.34 bitrate= 385.7kbits/frame= 1408 fps= 36 q=28.0 size=    2624kB time=00:00:56.27 bitrate= 382.0kbits/frame= 1426 fps= 36 q=28.0 size=    2821kB time=00:00:56.99 bitrate= 405.5kbits/frame= 1448 fps= 36 q=28.0 size=    2839kB time=00:00:57.88 bitrate= 401.7kbits/frame= 1464 fps= 36 q=28.0 size=    2853kB time=00:00:58.53 bitrate= 399.2kbits/frame= 1481 fps= 36 q=28.0 size=    2867kB time=00:00:59.22 bitrate= 396.5kbits/frame= 1495 fps= 36 q=28.0 size=    2877kB time=00:00:59.78 bitrate= 394.2kbits/frame= 1509 fps= 36 q=28.0 size=    2888kB time=00:01:00.29 bitrate= 392.4kbits/frame= 1522 fps= 36 q=28.0 size=    2901kB time=00:01:00.85 bitrate= 390.5kbits/frame= 1535 fps= 35 q=28.0 size=    2909kB time=00:01:01.36 bitrate= 388.4kbits/frame= 1548 fps= 35 q=28.0 size=    2919kB time=00:01:01.87 bitrate= 386.5kbits/frame= 1562 fps= 35 q=28.0 size=    2929kB time=00:01:02.45 bitrate= 384.2kbits/frame= 1583 fps= 35 q=28.0 size=    2952kB time=00:01:03.29 bitrate= 382.0kbits/frame= 1599 fps= 35 q=28.0 size=    2965kB time=00:01:03.91 bitrate= 380.0kbits/frame= 1618 fps= 35 q=28.0 size=    2980kB time=00:01:04.66 bitrate= 377.5kbits/frame= 1636 fps= 35 q=28.0 size=    3000kB time=00:01:05.42 bitrate= 375.6kbits/frame= 1653 fps= 35 q=28.0 size=    3011kB time=00:01:06.10 bitrate= 373.2kbits/frame= 1670 fps= 35 q=28.0 size=    3025kB time=00:01:06.77 bitrate= 371.1kbits/frame= 1688 fps= 35 q=28.0 size=    3225kB time=00:01:07.49 bitrate= 391.4kbits/frame= 1709 fps= 35 q=28.0 size=    3243kB time=00:01:08.32 bitrate= 388.8kbits/frame= 1731 fps= 35 q=28.0 size=    3260kB time=00:01:09.18 bitrate= 385.9kbits/frame= 1749 fps= 35 q=28.0 size=    3274kB time=00:01:09.93 bitrate= 383.6kbits/frame= 1769 fps= 35 q=28.0 size=    3291kB time=00:01:10.72 bitrate= 381.2kbits/frame= 1785 fps= 35 q=28.0 size=    3302kB time=00:01:11.37 bitrate= 379.0kbits/frame= 1801 fps= 35 q=28.0 size=    3362kB time=00:01:12.02 bitrate= 382.4kbits/frame= 1822 fps= 35 q=28.0 size=    3401kB time=00:01:12.85 bitrate= 382.4kbits/frame= 1836 fps= 35 q=28.0 size=    3428kB time=00:01:13.41 bitrate= 382.5kbits/frame= 1854 fps= 35 q=28.0 size=    3465kB time=00:01:14.13 bitrate= 382.9kbits/frame= 1876 fps= 35 q=28.0 size=    3486kB time=00:01:15.01 bitrate= 380.7kbits/frame= 1900 fps= 35 q=28.0 size=    3517kB time=00:01:15.96 bitrate= 379.2kbits/frame= 1921 fps= 35 q=28.0 size=    3543kB time=00:01:16.80 bitrate= 377.9kbits/frame= 1939 fps= 35 q=28.0 size=    3743kB time=00:01:17.54 bitrate= 395.5kbits/frame= 1959 fps= 35 q=28.0 size=    3770kB time=00:01:18.31 bitrate= 394.4kbits/frame= 1980 fps= 35 q=28.0 size=    3789kB time=00:01:19.17 bitrate= 392.1kbits/frame= 2000 fps= 35 q=28.0 size=    3811kB time=00:01:19.96 bitrate= 390.5kbits/frame= 2022 fps= 36 q=28.0 size=    3834kB time=00:01:20.84 bitrate= 388.5kbits/frame= 2039 fps= 36 q=28.0 size=    3851kB time=00:01:21.54 bitrate= 386.9kbits/frame= 2059 fps= 36 q=28.0 size=    3874kB time=00:01:22.33 bitrate= 385.4kbits/frame= 2075 fps= 36 q=28.0 size=    3888kB time=00:01:22.98 bitrate= 383.9kbits/frame= 2092 fps= 36 q=28.0 size=    3906kB time=00:01:23.63 bitrate= 382.6kbits/frame= 2109 fps= 35 q=28.0 size=    3931kB time=00:01:24.35 bitrate= 381.8kbits/frame= 2127 fps= 35 q=28.0 size=    3949kB time=00:01:25.07 bitrate= 380.3kbits/frame= 2141 fps= 35 q=28.0 size=    3963kB time=00:01:25.60 bitrate= 379.3kbits/frame= 2154 fps= 35 q=28.0 size=    3976kB time=00:01:26.11 bitrate= 378.2kbits/frame= 2169 fps= 35 q=28.0 size=    3990kB time=00:01:26.72 bitrate= 376.9kbits/frame= 2177 fps= 35 q=28.0 size=    4184kB time=00:01:27.04 bitrate= 393.7kbits/frame= 2191 fps= 35 q=28.0 size=    4197kB time=00:01:27.60 bitrate= 392.5kbits/frame= 2212 fps= 35 q=28.0 size=    4219kB time=00:01:28.46 bitrate= 390.7kbits/frame= 2227 fps= 35 q=28.0 size=    4233kB time=00:01:29.04 bitrate= 389.4kbits/frame= 2241 fps= 35 q=28.0 size=    4246kB time=00:01:29.59 bitrate= 388.2kbits/frame= 2255 fps= 35 q=28.0 size=    4266kB time=00:01:30.13 bitrate= 387.7kbits/frame= 2276 fps= 35 q=28.0 size=    4288kB time=00:01:31.01 bitrate= 385.9kbits/frame= 2297 fps= 35 q=28.0 size=    4308kB time=00:01:31.82 bitrate= 384.3kbits/frame= 2310 fps= 35 q=28.0 size=    4322kB time=00:01:32.36 bitrate= 383.3kbits/frame= 2323 fps= 35 q=28.0 size=    4337kB time=00:01:32.85 bitrate= 382.6kbits/frame= 2337 fps= 35 q=28.0 size=    4355kB time=00:01:33.45 bitrate= 381.7kbits/frame= 2355 fps= 35 q=28.0 size=    4377kB time=00:01:34.15 bitrate= 380.8kbits/frame= 2372 fps= 35 q=28.0 size=    4396kB time=00:01:34.82 bitrate= 379.8kbits/frame= 2386 fps= 35 q=28.0 size=    4407kB time=00:01:35.38 bitrate= 378.5kbits/frame= 2401 fps= 35 q=28.0 size=    4426kB time=00:01:35.98 bitrate= 377.7kbits/frame= 2418 fps= 35 q=28.0 size=    4440kB time=00:01:36.65 bitrate= 376.3kbits/frame= 2429 fps= 35 q=28.0 size=    4638kB time=00:01:37.09 bitrate= 391.3kbits/frame= 2444 fps= 35 q=28.0 size=    4655kB time=00:01:37.72 bitrate= 390.2kbits/frame= 2461 fps= 35 q=28.0 size=    4672kB time=00:01:38.39 bitrate= 388.9kbits/frame= 2481 fps= 35 q=28.0 size=    4693kB time=00:01:39.21 bitrate= 387.5kbits/frame= 2503 fps= 35 q=28.0 size=    4718kB time=00:01:40.07 bitrate= 386.2kbits/frame= 2523 fps= 35 q=28.0 size=    4741kB time=00:01:40.88 bitrate= 385.0kbits/frame= 2537 fps= 35 q=28.0 size=    4770kB time=00:01:41.44 bitrate= 385.2kbits/frame= 2557 fps= 35 q=28.0 size=    4792kB time=00:01:42.25 bitrate= 383.9kbits/frame= 2577 fps= 35 q=28.0 size=    4823kB time=00:01:43.04 bitrate= 383.4kbits/frame= 2598 fps= 35 q=28.0 size=    4843kB time=00:01:43.85 bitrate= 382.0kbits/frame= 2614 fps= 35 q=28.0 size=    4862kB time=00:01:44.50 bitrate= 381.1kbits/frame= 2633 fps= 35 q=28.0 size=    4884kB time=00:01:45.24 bitrate= 380.1kbits/frame= 2653 fps= 35 q=28.0 size=    4906kB time=00:01:46.08 bitrate= 378.9kbits/frame= 2673 fps= 35 q=28.0 size=    4922kB time=00:01:46.85 bitrate= 377.4kbits/frame= 2691 fps= 35 q=28.0 size=    5127kB time=00:01:47.57 bitrate= 390.4kbits/frame= 2715 fps= 35 q=28.0 size=    5152kB time=00:01:48.57 bitrate= 388.7kbits/frame= 2738 fps= 35 q=28.0 size=    5175kB time=00:01:49.45 bitrate= 387.3kbits/frame= 2762 fps= 35 q=28.0 size=    5199kB time=00:01:50.45 bitrate= 385.6kbits/frame= 2786 fps= 35 q=28.0 size=    5223kB time=00:01:51.37 bitrate= 384.2kbits/frame= 2809 fps= 35 q=28.0 size=    5250kB time=00:01:52.33 bitrate= 382.9kbits/frame= 2832 fps= 35 q=28.0 size=    5275kB time=00:01:53.21 bitrate= 381.7kbits/frame= 2846 fps= 35 q=28.0 size=    5287kB time=00:01:53.79 bitrate= 380.6kbits/frame= 2863 fps= 35 q=28.0 size=    5303kB time=00:01:54.46 bitrate= 379.5kbits/frame= 2884 fps= 35 q=28.0 size=    5329kB time=00:01:55.32 bitrate= 378.5kbits/frame= 2907 fps= 35 q=28.0 size=    5356kB time=00:01:56.25 bitrate= 377.4kbits/frame= 2926 fps= 35 q=28.0 size=    5560kB time=00:01:57.02 bitrate= 389.2kbits/frame= 2949 fps= 35 q=28.0 size=    5586kB time=00:01:57.92 bitrate= 388.1kbits/frame= 2972 fps= 35 q=28.0 size=    5613kB time=00:01:58.85 bitrate= 386.8kbits/frame= 2993 fps= 35 q=28.0 size=    5633kB time=00:01:59.69 bitrate= 385.6kbits/frame= 3015 fps= 35 q=28.0 size=    5660kB time=00:02:00.55 bitrate= 384.6kbits/frame= 3031 fps= 35 q=28.0 size=    5679kB time=00:02:01.20 bitrate= 383.8kbits/frame= 3050 fps= 35 q=28.0 size=    5696kB time=00:02:01.96 bitrate= 382.6kbits/frame= 3065 fps= 35 q=28.0 size=    5710kB time=00:02:02.57 bitrate= 381.7kbits/frame= 3082 fps= 35 q=28.0 size=    5726kB time=00:02:03.26 bitrate= 380.5kbits/frame= 3105 fps= 35 q=28.0 size=    5750kB time=00:02:04.17 bitrate= 379.3kbits/frame= 3127 fps= 35 q=28.0 size=    5774kB time=00:02:05.05 bitrate= 378.2kbits/frame= 3148 fps= 35 q=28.0 size=    5797kB time=00:02:05.89 bitrate= 377.2kbits/frame= 3171 fps= 35 q=28.0 size=    5819kB time=00:02:06.82 bitrate= 375.9kbits/frame= 3189 fps= 35 q=28.0 size=    6021kB time=00:02:07.51 bitrate= 386.8kbits/frame= 3211 fps= 35 q=28.0 size=    6044kB time=00:02:08.39 bitrate= 385.6kbits/frame= 3226 fps= 35 q=28.0 size=    6058kB time=00:02:08.98 bitrate= 384.7kbits/frame= 3244 fps= 35 q=28.0 size=    6073kB time=00:02:09.72 bitrate= 383.5kbits/frame= 3266 fps= 36 q=28.0 size=    6096kB time=00:02:10.60 bitrate= 382.4kbits/frame= 3289 fps= 36 q=28.0 size=    6120kB time=00:02:11.51 bitrate= 381.3kbits/frame= 3313 fps= 36 q=28.0 size=    6147kB time=00:02:12.50 bitrate= 380.0kbits/frame= 3326 fps= 36 q=28.0 size=    6164kB time=00:02:13.02 bitrate= 379.6kbits/frame= 3342 fps= 36 q=28.0 size=    6179kB time=00:02:13.64 bitrate= 378.7kbits/frame= 3358 fps= 35 q=28.0 size=    6193kB time=00:02:14.29 bitrate= 377.8kbits/frame= 3377 fps= 35 q=28.0 size=    6214kB time=00:02:15.06 bitrate= 376.9kbits/frame= 3393 fps= 35 q=28.0 size=    6229kB time=00:02:15.69 bitrate= 376.1kbits/frame= 3408 fps= 35 q=28.0 size=    6243kB time=00:02:16.29 bitrate= 375.3kbits/frame= 3426 fps= 35 q=28.0 size=    6451kB time=00:02:17.01 bitrate= 385.7kbits/frame= 3440 fps= 35 q=28.0 size=    6466kB time=00:02:17.57 bitrate= 385.0kbits/frame= 3455 fps= 35 q=28.0 size=    6480kB time=00:02:18.17 bitrate= 384.2kbits/frame= 3469 fps= 35 q=28.0 size=    6494kB time=00:02:18.73 bitrate= 383.4kbits/frame= 3483 fps= 35 q=28.0 size=    6507kB time=00:02:19.29 bitrate= 382.7kbits/frame= 3506 fps= 35 q=28.0 size=    6531kB time=00:02:20.21 bitrate= 381.5kbits/frame= 3521 fps= 35 q=28.0 size=    6545kB time=00:02:20.82 bitrate= 380.7kbits/frame= 3544 fps= 35 q=28.0 size=    6569kB time=00:02:21.75 bitrate= 379.7kbits/frame= 3567 fps= 35 q=28.0 size=    6593kB time=00:02:22.63 bitrate= 378.7kbits/frame= 3590 fps= 35 q=28.0 size=    6617kB time=00:02:23.56 bitrate= 377.6kbits/frame= 3613 fps= 35 q=28.0 size=    6637kB time=00:02:24.49 bitrate= 376.3kbits/frame= 3635 fps= 35 q=28.0 size=    6662kB time=00:02:25.37 bitrate= 375.4kbits/frame= 3658 fps= 35 q=28.0 size=    6688kB time=00:02:26.30 bitrate= 374.5kbits/frame= 3676 fps= 35 q=28.0 size=    6886kB time=00:02:26.99 bitrate= 383.7kbits/frame= 3701 fps= 36 q=28.0 size=    6919kB time=00:02:27.99 bitrate= 383.0kbits/frame= 3725 fps= 36 q=28.0 size=    6940kB time=00:02:28.97 bitrate= 381.7kbits/frame= 3749 fps= 36 q=28.0 size=    6966kB time=00:02:29.90 bitrate= 380.7kbits/frame= 3770 fps= 36 q=28.0 size=    6987kB time=00:02:30.78 bitrate= 379.6kbits/frame= 3793 fps= 36 q=28.0 size=    7011kB time=00:02:31.68 bitrate= 378.6kbits/frame= 3817 fps= 36 q=28.0 size=    7035kB time=00:02:32.61 bitrate= 377.6kbits/frame= 3841 fps= 36 q=28.0 size=    7059kB time=00:02:33.59 bitrate= 376.5kbits/frame= 3864 fps= 36 q=28.0 size=    7079kB time=00:02:34.52 bitrate= 375.3kbits/frame= 3886 fps= 36 q=28.0 size=    7108kB time=00:02:35.40 bitrate= 374.7kbits/frame= 3903 fps= 36 q=28.0 size=    7122kB time=00:02:36.10 bitrate= 373.8kbits/frame= 3921 fps= 36 q=28.0 size=    7142kB time=00:02:36.79 bitrate= 373.1kbits/frame= 3935 fps= 36 q=28.0 size=    7344kB time=00:02:37.37 bitrate= 382.3kbits/frame= 3953 fps= 36 q=28.0 size=    7362kB time=00:02:38.07 bitrate= 381.5kbits/frame= 3976 fps= 36 q=28.0 size=    7389kB time=00:02:39.00 bitrate= 380.7kbits/frame= 3991 fps= 36 q=28.0 size=    7402kB time=00:02:39.60 bitrate= 379.9kbits/frame= 4014 fps= 36 q=28.0 size=    7428kB time=00:02:40.51 bitrate= 379.1kbits/frame= 4036 fps= 36 q=28.0 size=    7457kB time=00:02:41.39 bitrate= 378.5kbits/frame= 4051 fps= 36 q=28.0 size=    7471kB time=00:02:41.99 bitrate= 377.8kbits/frame= 4075 fps= 36 q=28.0 size=    7496kB time=00:02:42.95 bitrate= 376.9kbits/frame= 4091 fps= 36 q=28.0 size=    7511kB time=00:02:43.62 bitrate= 376.0kbits/frame= 4110 fps= 36 q=28.0 size=    7533kB time=00:02:44.36 bitrate= 375.5kbits/frame= 4123 fps= 36 q=28.0 size=    7551kB time=00:02:44.87 bitrate= 375.2kbits/frame= 4144 fps= 36 q=28.0 size=    7569kB time=00:02:45.71 bitrate= 374.2kbits/frame= 4160 fps= 36 q=28.0 size=    7589kB time=00:02:46.34 bitrate= 373.7kbits/frame= 4172 fps= 36 q=28.0 size=    7601kB time=00:02:46.85 bitrate= 373.2kbits/frame= 4185 fps= 36 q=28.0 size=    7801kB time=00:02:47.36 bitrate= 381.9kbits/frame= 4208 fps= 36 q=28.0 size=    7822kB time=00:02:48.26 bitrate= 380.8kbits/frame= 4226 fps= 36 q=28.0 size=    7843kB time=00:02:48.98 bitrate= 380.2kbits/frame= 4248 fps= 36 q=28.0 size=    7863kB time=00:02:49.89 bitrate= 379.1kbits/frame= 4269 fps= 36 q=28.0 size=    7888kB time=00:02:50.72 bitrate= 378.5kbits/frame= 4286 fps= 36 q=28.0 size=    7911kB time=00:02:51.40 bitrate= 378.1kbits/frame= 4309 fps= 36 q=28.0 size=    7932kB time=00:02:52.33 bitrate= 377.1kbits/frame= 4325 fps= 36 q=28.0 size=    7951kB time=00:02:52.93 bitrate= 376.6kbits/frame= 4346 fps= 36 q=28.0 size=    7970kB time=00:02:53.81 bitrate= 375.6kbits/frame= 4366 fps= 36 q=28.0 size=    7990kB time=00:02:54.60 bitrate= 374.9kbits/frame= 4388 fps= 36 q=28.0 size=    8013kB time=00:02:55.48 bitrate= 374.1kbits/frame= 4410 fps= 36 q=28.0 size=    8040kB time=00:02:56.37 bitrate= 373.4kbits/frame= 4426 fps= 36 q=28.0 size=    8235kB time=00:02:57.02 bitrate= 381.1kbits/frame= 4451 fps= 36 q=28.0 size=    8259kB time=00:02:58.02 bitrate= 380.1kbits/frame= 4471 fps= 36 q=28.0 size=    8277kB time=00:02:58.81 bitrate= 379.2kbits/frame= 4492 fps= 36 q=28.0 size=    8300kB time=00:02:59.64 bitrate= 378.5kbits/frame= 4511 fps= 36 q=28.0 size=    8318kB time=00:03:00.41 bitrate= 377.7kbits/frame= 4526 fps= 36 q=28.0 size=    8332kB time=00:03:01.01 bitrate= 377.0kbits/frame= 4539 fps= 36 q=28.0 size=    8352kB time=00:03:01.52 bitrate= 376.9kbits/frame= 4558 fps= 36 q=28.0 size=    8369kB time=00:03:02.29 bitrate= 376.1kbits/frame= 4572 fps= 36 q=28.0 size=    8382kB time=00:03:02.85 bitrate= 375.5kbits/frame= 4588 fps= 36 q=28.0 size=    8397kB time=00:03:03.47 bitrate= 374.9kbits/frame= 4603 fps= 36 q=28.0 size=    8417kB time=00:03:04.08 bitrate= 374.6kbits/frame= 4616 fps= 36 q=28.0 size=    8426kB time=00:03:04.61 bitrate= 373.9kbits/frame= 4628 fps= 36 q=28.0 size=    8440kB time=00:03:05.07 bitrate= 373.6kbits/frame= 4641 fps= 36 q=28.0 size=    8456kB time=00:03:05.61 bitrate= 373.2kbits/frame= 4655 fps= 36 q=28.0 size=    8470kB time=00:03:06.17 bitrate= 372.7kbits/frame= 4669 fps= 36 q=28.0 size=    8483kB time=00:03:06.72 bitrate= 372.1kbits/frame= 4681 fps= 36 q=28.0 size=    8679kB time=00:03:07.21 bitrate= 379.7kbits/frame= 4695 fps= 35 q=28.0 size=    8692kB time=00:03:07.75 bitrate= 379.3kbits/frame= 4709 fps= 35 q=28.0 size=    8706kB time=00:03:08.33 bitrate= 378.7kbits/frame= 4723 fps= 35 q=28.0 size=    8719kB time=00:03:08.88 bitrate= 378.2kbits/frame= 4727 fps= 35 q=10353281.0 Lsize=    8928kB time=00:03:09.07 bitrate= 386.8kbits/s dup=2 drop=0    
video:5817kB audio:2954kB subtitle:0 global headers:0kB muxing overhead 1.781257%
[libx264 @ 0xaa1b720] frame I:25    Avg QP:13.24  size:161636
[libx264 @ 0xaa1b720] frame P:1200  Avg QP:19.90  size:  1374
[libx264 @ 0xaa1b720] frame B:3502  Avg QP:28.70  size:    76
[libx264 @ 0xaa1b720] consecutive B-frames:  1.2%  0.1%  0.3% 98.5%
[libx264 @ 0xaa1b720] mb I  I16..4:  9.2% 71.7% 19.1%
[libx264 @ 0xaa1b720] mb P  I16..4:  0.1%  0.0%  0.1%  P16..4:  0.4%  0.1%  0.1%  0.0%  0.0%    skip:99.1%
[libx264 @ 0xaa1b720] mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  0.6%  0.0%  0.0%  direct: 0.0%  skip:99.4%  L0:51.0% L1:48.7% BI: 0.3%
[libx264 @ 0xaa1b720] 8x8 transform intra:66.8% inter:19.6%
[libx264 @ 0xaa1b720] coded y,u,v intra: 77.7% 10.9% 10.9% inter: 0.1% 0.0% 0.0%
[libx264 @ 0xaa1b720] i16 v,h,dc,p: 37% 60%  3%  0%
[libx264 @ 0xaa1b720] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu:  7% 26% 43% 12%  5%  1%  2%  1%  3%
[libx264 @ 0xaa1b720] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 26% 27% 13%  6%  6%  5%  6%  6%  6%
[libx264 @ 0xaa1b720] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0xaa1b720] ref P L0: 76.9%  6.3% 13.1%  3.8%
[libx264 @ 0xaa1b720] ref B L0: 71.8% 27.2%  1.0%
[libx264 @ 0xaa1b720] ref B L1: 96.6%  3.4%
[libx264 @ 0xaa1b720] kb/s:252.00

```

---

### Post by mapes12 on 2013-02-26
There's a package out there called Record my desktop. I can't remember what format the output is but I've uploaded to YouTube without any problem in the past.

---

### Post by cyb3r_sn4k3 on 2013-02-26
> **mapes12 said:**
> There's a package out there called Record my desktop. I can't remember what format the output is but I've uploaded to YouTube without any problem in the past.

Thanks for the info. But I would really like to know whats wrong as I might need ffmpeg to convert something then upload to youtube in the future.

---

### Post by FakeOutdoorsman on 2013-02-26
> **cyb3r_sn4k3 said:**
> Output for ffmpeg -i hope.mkv test.mp4
```

Stream #0:0(und): Video: h264 (High 4:4:4 Predictive), yuv444p

```

YouTube does not accept H.264 with yuv444p. YouTube does accept H.264 (lossless or lossy), yuv420p.

Your commands using "-crf 0", when recording your desktop, create a lossless output with yuv444p.

Generally, you want to capture as fast as possible without having to work on compressing things very much. This means you usually make a lossless output first so you can achieve your desired capturing framerate (assuming your CPU is the bottleneck). You then re-encode this temporary, large, lossless output to a more manageable size for uploading.

When re-encoding for upload you should add **-pix_fmt yuv420p**, otherwise, if your input is yuv444p then ffmpeg will attempt to preserve that, and that is not supported by YouTube apparently as of now.

So to summarize:
[list=1]
[*]Record your desktop using the lossless method for speed of capture. However, if your computer can handle it, then you can skip this and record directly to the lossy output (change "-crf 0" to "-crf 18" and also add "-pix_fmt yuv420p").
[*]Re-encode the lossless file to a lossy file so it won't take 14 years to upload; using the "-pix_fmt yuv420" option:
[/list]
```
ffmpeg -i lossless.mkv -vcodec libx264 -crf 18 -pix_fmt yuv420p -acodec copy output.mkv
```

Also see:
[list]
[*][FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide)
[*][How to Encode Videos for YouTube and other Video Sharing Sites](https://ffmpeg.org/trac/ffmpeg/wiki/EncodeforYouTube)
[/list]

---

### Post by cyb3r_sn4k3 on 2013-02-27
> **FakeOutdoorsman said:**
> YouTube does not accept H.264 with yuv444p. YouTube does accept H.264 (lossless or lossy), yuv420p.

Your commands using "-crf 0", when recording your desktop, create a lossless output with yuv444p.

Generally, you want to capture as fast as possible without having to work on compressing things very much. This means you usually make a lossless output first so you can achieve your desired capturing framerate (assuming your CPU is the bottleneck). You then re-encode this temporary, large, lossless output to a more manageable size for uploading.

When re-encoding for upload you should add **-pix_fmt yuv420p**, otherwise, if your input is yuv444p then ffmpeg will attempt to preserve that, and that is not supported by YouTube apparently as of now.

So to summarize:
[LIST=1]
[*]Record your desktop using the lossless method for speed of capture. However, if your computer can handle it, then you can skip this and record directly to the lossy output (change "-crf 0" to "-crf 18" and also add "-pix_fmt yuv420p").
[*]Re-encode the lossless file to a lossy file so it won't take 14 years to upload; using the "-pix_fmt yuv420" option:
[/LIST]
```
ffmpeg -i lossless.mkv -vcodec libx264 -crf 18 -pix_fmt yuv420p -acodec copy output.mkv
```Also see:
[LIST]
[*][FFmpeg and x264 Encoding Guide]("https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide")
[*][How to Encode Videos for YouTube and other Video Sharing Sites]("https://ffmpeg.org/trac/ffmpeg/wiki/EncodeforYouTube")
[/LIST]


It Works! Thanks a lot.:p

---

