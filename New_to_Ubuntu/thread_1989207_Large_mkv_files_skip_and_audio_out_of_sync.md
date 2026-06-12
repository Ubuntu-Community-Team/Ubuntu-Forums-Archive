---
title: "Large mkv files skip and audio out of sync"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by Donal Smith on 2012-05-28
Ok, so struggling to play a 1.4GB .mkv video file without it skipping and the audio going out of sync. I have tried:

[LIST]
[*]Media players: VLC, Totem and mplayer2 via smplayer.
[*]Booting into my Windows XP partition. No luck with WMP or VLC 2.0.1
[/LIST]

Not an exhaustive list, but my expertise in this area is limited. 

Running Ubuntu 12.04 on a netbook: Processor: Intel® Atom™ CPU N270 @ 1.60GHz × 2, Graphics: Intel® 945GME x86/MMX/SSE2

Is it just too much for the machine? If that is the case, can I convert/reduce the file somehow to get it to work?

Many thanks!

Donal.

---

### Post by django0909 on 2012-05-28
I'll assume you've tried more than one mkv file?

---

### Post by Donal Smith on 2012-05-28
Yup! Although they're all from pretty much the same source.

---

### Post by django0909 on 2012-05-28
How much RAM is installed in the system? Mine runs mkv's fine on a Celeron M processor in Lubuntu, however I have 2GB of ram installed so that might be it. Try installing Lubuntu Desktop or running an XFCE session, see if it frees things up a bit?

---

### Post by Cheesemill on 2012-05-28
I think it's just a case of the Atom CPU not being powerful enough to decode HD video.

---

### Post by qyot27 on 2012-05-28
> **Cheesemill said:**
> I think it's just a case of the Atom CPU not being powerful enough to decode HD video.
More than likely this, even though the OP never specified what the resolution (and therefore if it really is HD) or framerate was.  A size of 1.4 GB could very well be a movie-length SD video.

Solutions include (assuming the video is both H.264 and either 720p or 1080p):
1) Transcoding to a less burdensome set of features within H.264 (such as using x264's --preset ultrafast --tune zerolatency settings - it'll massively inflate the filesize, but it'll be much easier to decode in software)
2) Downscaling to 480p (probably the most significant way to ease decoding burden)
3) Transcoding to MPEG-4 Advanced Simple Profile (a.k.a. Xvid)
4) A combination of points 1 and 2 or points 2 and 3.

All of these things can be done by using x264 (sans #3) and/or FFmpeg.



And while I didn't mention it, overhead from subtitle rendering (if any) can screw with it.  There's not much that can help that, short of hardcoding them into the video (which requires either mplayer2's vo-lavc branch or AviSynth on Windows if you want to do it with minimal fussing while retaining any subtitle styling).  I also remember some reports of the repo version of mplayer2 being a bit, well, wonky.  Building it yourself (in which case you may as well build the vo-lavc branch) generally resolves this.

---

### Post by Donal Smith on 2012-05-28
Clarifications: Memory: 991.6 MiB. Video resolution: 720p. Framerate: 24fps.

@django0909: Yes an XFCE session did indeed "free things up a bit." It's not perfect, still struggles in parts, but is *significantly* better. Perhaps I oughta install Lubuntu when I get the chance.

@Cheesemill: That's what I was worried about. Does a dramatically better performance under XFCE indicate that it's just about capable though?

@qyot27: Yeah, I suspected something like this might be necessary. Let's say I, or somebody similarly wet behind the ears in this whole area, wanted to go down this road. Could you provide, or direct me towards, simple instructions on how do perform these tasks?

Thanks so much for all the help guys!

---

### Post by qyot27 on 2012-05-29
> **Donal Smith said:**
> @qyot27: Yeah, I suspected something like this might be necessary. Let's say I, or somebody similarly wet behind the ears in this whole area, wanted to go down this road. Could you provide, or direct me towards, simple instructions on how do perform these tasks?
As forewarning, Ubuntu switched to the 'libav' fork of FFmpeg, so I'm not sure if the actual 'ffmpeg' command is still present with the repo versions.  But you could follow [this guide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) to compile and install x264 and the actual main FFmpeg (which also gets you updates that the repo versions might not have).




Assuming that there's no downscaling and no subtitles:
```
ffmpeg -i input.mkv -vcodec libx264 -crf 18 -preset ultrafast -tune zerolatency -acodec copy output.mkv
```

With downscaling:
```
ffmpeg -i input.mkv -vcodec libx264 -crf 18 -preset ultrafast -tune zerolatency -s 848x480 -acodec copy output.mkv
```

Using x264 to do it (assumes x264 was compiled with LAVF or FFMS2 support):
```
ffmpeg -i input.mkv -vn -acodec copy output.mp4

x264 --preset ultrafast --tune zerolatency --crf 18 -o output.mkv input.mkv

ffmpeg -i output.mkv -i output.mp4 -vcodec copy -acodec copy finaloutput.mkv
```

With downscaling:
```
ffmpeg -i input.mkv -vn -acodec copy output.mp4

x264 --preset ultrafast --tune zerolatency --crf 18 --vf resize:848,480 -o output.mkv input.mkv

ffmpeg -i output.mkv -i output.mp4 -vcodec copy -acodec copy finaloutput.mkv
```

Converting to Xvid (requires an FFmpeg with libxvidcore compiled in; otherwise, replace 'libxvid' with 'mpeg4' and hope the configuration options still work):
```
ffmpeg -i input.mkv -vcodec libxvid -b:v 4000k -bf 0 -flags cgop -subq 3 -bufsize 0 -mbd simple -me_method log -acodec libmp3lame -b:a 192k -vtag DX50 output.avi
```

With downscaling:
```
ffmpeg -i input.mkv -vcodec libxvid -b:v 4000k -bf 0 -flags cgop -subq 3 -bufsize 0 -mbd simple -me_method log -s 848x480 -acodec libmp3lame -b:a 192k -vtag DX50 output.avi
```

For hardcoding subtitles (requires mplayer2's vo-lavc branch, which you'll have to compile yourself, as I'm unaware of any PPAs that provide it):
with x264:
```
ffmpeg -i input.mkv -vn -acodec copy output.mp4

mplayer -nosound input.mkv -o output.mkv -ofps 23.976 -ovc libx264 -ovcopts preset=ultrafast,tune=zerolatency,crf=18

ffmpeg -i input.mkv -i output.mp4 -vcodec copy -acodec copy finaloutput.mkv
```

with Xvid (and downscaling):
```
ffmpeg -i input.mkv -vn -acodec libmp3lame -b:a 192k output.mp3

mplayer -vf scale=854:480 -sws 0 -nosound input.mkv -o output.avi -ofps 23.976 -ovc libxvid -ovcopts b=4000k,bf=0,flags=cgop,subq=3,bufsize=0,mbd=simple,me_method=log

ffmpeg -i output.avi -i output.mp3 -vcodec copy -acodec copy -vtag DX50 finaloutput.avi
```
Audio for the Xvid files converted to MP3 for compatibility reasons.  Requires that the FFmpeg was compiled with libmp3lame support.



The above are really just targeted for speed of encoding and the assurance that it'll probably play on most things, but not for archiving or tweaking the visual quality: they'll look decent, and are just meant as throwaway encodes that you do because you need to play something on a machine too weak to handle the original source file.

---

### Post by FakeOutdoorsman on 2012-05-29
> **qyot27 said:**
> Solutions include (assuming the video is both H.264 and either 720p or 1080p):
1) Transcoding to a less burdensome set of features within H.264 (such as using x264's --preset ultrafast --tune zerolatency settings - it'll massively inflate the filesize, but it'll be much easier to decode in software)

There is also *-tune fastdecode* which is worth a try.

---

### Post by qyot27 on 2012-05-29
> **FakeOutdoorsman said:**
> There is also *-tune fastdecode* which is worth a try.
Using fastdecode with ultrafast would be redundant because all of the settings it uses are also set by ultrafast (although it would make sense if any of the presets above ultrafast were used).

For that matter, half of the zerolatency tuning is also covered by ultrafast, so it might very well be redundant (if the three remaining parameters don't really have an impact of decoding time, although they would have an impact for use in editing programs or streaming, where extremely low latency is desired).

--preset ultrafast:
--no-8x8dct --aq-mode 0 --b-adapt 0 *--bframes 0* **--no-cabac** **--no-deblock** *--no-mbtree* --me dia --no-mixed-refs --partitions none *--rc-lookahead 0* --ref 1 --scenecut 0 --subme 0 --trellis 0 **--no-weightb --weightp 0**

--tune fastdecode:
**--no-cabac --no-deblock --no-weightb --weightp 0**

--tune zerolatency:
*--bframes 0* --force-cfr *--no-mbtree* --sync-lookahead 0 --sliced-threads *--rc-lookahead 0*

---

### Post by FakeOutdoorsman on 2012-05-29
It would be interesting to see if there is a difference in decoding performance between the two.
```
ffmpeg -benchmark -i input -f null -
```
Unfortunately my similar Atom machine fell down some stairs.

---

### Post by qyot27 on 2012-05-29
Now, take into consideration the hardware here (being far older than an Atom-based netbook), since CPUs with SSE2 support could make a difference in decoding speed, but it seems like ultrafast on its own is very marginally faster than ultrafast/zerolatency.

I encoded the same file twice, differing only in the use of --tune zerolatency.  I had to run these tests on Windows, but I don't think that factors into it too much.  The x264 encoding times might be a little off because the first encode was done while I still had the file manager open.

Celeron Coppermine 1GHz (32KB L1, 128KB L2, 100 MT/s FSB), 512 MBs PC133 SDRAM
```
x264 --preset ultrafast --tune zerolatency --crf 18 -o test_zerolatency.mkv test.avs
avs [info]: 848x480p 0:0 @ 24000/1001 fps (cfr)
avs [info]: color matrix: undef
x264 [info]: using cpu capabilities: MMX2 Cache32
x264 [info]: profile Constrained Baseline, level 3.0
x264 [info]: started at Tue May 29 20:34:32 2012
x264 [info]: frame I:24    Avg QP:13.17  size: 47547
x264 [info]: frame P:5789  Avg QP:16.27  size: 14764
x264 [info]: mb I  I16..4: 100.0%  0.0%  0.0%
x264 [info]: mb P  I16..4: 26.7%  0.0%  0.0%  P16..4: 52.3%  0.0%  0.0%  0.0%  0.0%    skip:21.0%
x264 [info]: coded y,uvDC,uvAC intra: 25.4% 50.0% 19.0% inter: 34.9% 43.8% 8.3%
x264 [info]: i16 v,h,dc,p: 48% 26% 14% 13%
x264 [info]: i8c dc,h,v,p: 48% 22% 20% 10%
x264 [info]: kb/s:2857.86

encoded 5813 frames, 8.8562 fps, 2857.88 kb/s, 82.60 MB
x264 [info]: ended at Tue May 29 20:45:28 2012
x264 [info]: encoding duration 0:10:56

x264 --preset ultrafast --crf 18 -o test_onlyultrafast.mkv test.avs
avs [info]: 848x480p 0:0 @ 24000/1001 fps (cfr)
avs [info]: color matrix: undef
x264 [info]: using cpu capabilities: MMX2 Cache32
x264 [info]: profile Constrained Baseline, level 3.0
x264 [info]: started at Tue May 29 20:46:08 2012
x264 [info]: frame I:24    Avg QP:13.17  size: 47547
x264 [info]: frame P:5789  Avg QP:16.27  size: 14764
x264 [info]: mb I  I16..4: 100.0%  0.0%  0.0%
x264 [info]: mb P  I16..4: 26.7%  0.0%  0.0%  P16..4: 52.3%  0.0%  0.0%  0.0%  0.0%    skip:21.0%
x264 [info]: coded y,uvDC,uvAC intra: 25.4% 50.0% 19.0% inter: 34.9% 43.8% 8.3%
x264 [info]: i16 v,h,dc,p: 48% 26% 14% 13%
x264 [info]: i8c dc,h,v,p: 48% 22% 20% 10%
x264 [info]: kb/s:2857.86

encoded 5813 frames, 9.3314 fps, 2857.88 kb/s, 82.60 MB
x264 [info]: ended at Tue May 29 20:56:31 2012
x264 [info]: encoding duration 0:10:23
```


The FFmpeg benchmarks.
```
ffmpeg -benchmark -i test_zerolatency.mkv -f null -
ffmpeg version r41066 git-ab7d6cb Copyright (c) 2000-2012 the FFmpeg developers
  built on May 26 2012 21:31:41 with gcc 4.6.2
  configuration: --prefix=/home/qyot27/win32_build --cross-prefix=i686-w64-mingw32- --enable-gpl --enable-version3 --disable-w32threads --enable-memalign-hack --disable-decoder=utvideo --enable-libutvideo --enable-libxvid --disable-encoder=mpeg4 --enable-avisynth --cpu=pentium3 --extra-cflags='-I/home/qyot27/win32_build/include -march=pentium3 -mtune=pentium3 -DPTW32_STATIC_LIB' --extra-ldflags=-L/home/qyot27/win32_build/lib --target-os=mingw32 --arch=x86
  libavutil      51. 55.100 / 51. 55.100
  libavcodec     54. 23.100 / 54. 23.100
  libavformat    54.  6.101 / 54.  6.101
  libavdevice    54.  0.100 / 54.  0.100
  libavfilter     2. 77.100 /  2. 77.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, matroska,webm, from 'test_zerolatency.mkv':
  Duration: 00:04:02.45, start: 0.000000, bitrate: 2859 kb/s
    Stream #0:0(eng): Video: h264 (Constrained Baseline), yuv420p, 848x480, SAR 1:1 DAR 53:30, 23.98 fps, 23.98 tbr, 20k tbn, 47.95 tbc (default)
[buffer @ 019fda40] w:848 h:480 pixfmt:yuv420p tb:1/20000 sar:1/1 sws_param:flags=2
[buffersink @ 01ae8580] No opaque field provided
Output #0, null, to 'pipe:':
  Metadata:
    encoder         : Lavf54.6.101
    Stream #0:0(eng): Video: rawvideo (I420 / 0x30323449), yuv420p, 848x480 [SAR 1:1 DAR 53:30], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc (default)
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> rawvideo)
Press [q] to stop, [?] for help
[null @ 01c24020] Encoder did not produce proper pts, making some up.
frame= 5813 fps= 64 q=0.0 Lsize=       0kB time=00:04:02.45 bitrate=   0.0kbits/s
video:0kB audio:0kB global headers:0kB muxing overhead nan%
Output file is empty, nothing was encoded (check -ss / -t / -frames parameters if used)
bench: utime=82.016s maxrss=12376kB

ffmpeg -benchmark -i test_onlyultrafast.mkv -f null -
ffmpeg version r41066 git-ab7d6cb Copyright (c) 2000-2012 the FFmpeg developers
  built on May 26 2012 21:31:41 with gcc 4.6.2
  configuration: --prefix=/home/qyot27/win32_build --cross-prefix=i686-w64-mingw32- --enable-gpl --enable-version3 --disable-w32threads --enable-memalign-hack --disable-decoder=utvideo --enable-libutvideo --enable-libxvid --disable-encoder=mpeg4 --enable-avisynth --cpu=pentium3 --extra-cflags='-I/home/qyot27/win32_build/include -march=pentium3 -mtune=pentium3 -DPTW32_STATIC_LIB' --extra-ldflags=-L/home/qyot27/win32_build/lib --target-os=mingw32 --arch=x86
  libavutil      51. 55.100 / 51. 55.100
  libavcodec     54. 23.100 / 54. 23.100
  libavformat    54.  6.101 / 54.  6.101
  libavdevice    54.  0.100 / 54.  0.100
  libavfilter     2. 77.100 /  2. 77.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, matroska,webm, from 'test_onlyultrafast.mkv':
  Duration: 00:04:02.45, start: 0.000000, bitrate: 2859 kb/s
    Stream #0:0(eng): Video: h264 (Constrained Baseline), yuv420p, 848x480, SAR 1:1 DAR 53:30, 23.98 fps, 23.98 tbr, 20k tbn, 47.95 tbc (default)
[buffer @ 019fda60] w:848 h:480 pixfmt:yuv420p tb:1/20000 sar:1/1 sws_param:flags=2
[buffersink @ 01ae8580] No opaque field provided
Output #0, null, to 'pipe:':
  Metadata:
    encoder         : Lavf54.6.101
    Stream #0:0(eng): Video: rawvideo (I420 / 0x30323449), yuv420p, 848x480 [SAR 1:1 DAR 53:30], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc (default)
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> rawvideo)
Press [q] to stop, [?] for help
[null @ 01c24020] Encoder did not produce proper pts, making some up.
frame= 5813 fps= 65 q=0.0 Lsize=       0kB time=00:04:02.45 bitrate=   0.0kbits/s
video:0kB audio:0kB global headers:0kB muxing overhead nan%
Output file is empty, nothing was encoded (check -ss / -t / -frames parameters if used)
bench: utime=81.484s maxrss=12392kB
```




Okay, now for the spooky part: the encode features appear to be *absolutely the same*.  Meaning, even though zerolatency gets specified, it isn't being used.  Furthermore, and what prompted the 'spooky' comment, the two encodes have the same MD5 checksum.  Whatever's going on is making it result in extremely deterministic encodes.

---

### Post by FakeOutdoorsman on 2012-06-01
> **qyot27 said:**
> Okay, now for the spooky part: the encode features appear to be *absolutely the same*.  Meaning, even though zerolatency gets specified, it isn't being used.  Furthermore, and what prompted the 'spooky' comment, the two encodes have the same MD5 checksum.  Whatever's going on is making it result in extremely deterministic encodes.

Only difference for me using ultrafast on i7 860 @ 2.80GHz are threads, lookahead_threads, sliced_threads, and slices. Perhaps it makes sense given your older hardware. Of course the differences would be greater with a preset that uses b-frames and mb-tree.
```
$ strings ultrafast.mkv | grep x264
x264 r2200 999b753*
x264 - core 125 r2200 999b753 - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=12 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=23 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=18.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=0

$ strings ultrafast-zerolatency.mkv | grep x264
x264 r2200 999b753*
x264 - core 125 r2200 999b753 - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=8 lookahead_threads=8 sliced_threads=1 slices=8 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=23 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=18.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=0
```

Just out of curiosity, what WM are you using (if any) on that graybeard laptop?

---

### Post by qyot27 on 2012-06-01
> **FakeOutdoorsman said:**
> Just out of curiosity, what WM are you using (if any) on that graybeard laptop?
It's a desktop, actually (an upgraded beyond stock* eMachines T1110, ca. 2001).  But LXDE with [Compton](https://github.com/chjj/compton).  Unity 3D can run ok - if slowly - for the short time it takes between initial install and pulling in LXDE.

Takes over an hour just to compile FFmpeg, approx. 4 hours if I go through my typical cross-compiling routine of minimal FFmpeg->FFMS2 AviSynth C-plugin->FFMS2->x264 8bit->x264 9bit->x264 10bit->full FFmpeg.  Sure, I could cut the 9bit out since it never gets used, but I do it for kicks.

*switched out the hard drive from a 30GB 5400rpm to a 160GB 7200rpm, it's on its third power supply, GeForce 6200 PCI card (no AGP ports), swapped out the modem card for an ethernet card, added a USB 2.0 card, and added a DVD-R drive to go along with the CD-R drive it came with (and the DVD-R actually took the place of a DVD-ROM drive I'd salvaged from another computer we were getting rid of).  Also some peripheral things that don't really count much toward the core performance of the computer.

---

### Post by FakeOutdoorsman on 2012-06-02
Nice. I've always like the idea of old hardware still chugging along. I still have a tiny PII used as an in-house server at work for some little tasks. Does the job just fine.

---

### Post by qyot27 on 2012-06-02
Well, my computer is only the second-oldest one in the house.  We also have an NEC that my parents bought in 1995 - for almost $5000, if I recall correctly.  Has an original generation Pentium in it (maybe a P54CS?).  It can still run if we wanted it to, but it's physically blocked into a corner.  I used it as my main computer before I got this one.  Takes 10 minutes to boot into Windows 95.

Sure, it'd be little more than a glorified word processor these days, although from first-hand experience it could be a jukebox, or play the standard Solitaire/Minesweeper/Hearts/etc. stuff.  The 3 or 4 GB hard drive in it sort of limits that.

---

