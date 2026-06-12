---
title: "Reading a file using tac that is open and being written to by stdout"
date: 2010-05-10
forum: Programming Talk
---

### Post by prupert on 2010-05-10
Hi, so I am trying to write a simple (!) script that will give me the progress of a certain task, in this case it is converting a video using ffmpeg, but the principle can be applied to any task that produces output via stdout. The thinking goes, I take a final value, I then read the stdout that shows the progress towards that value and then calculate the percentage difference and print that (so, if copying a file, for example, I would take the size of the source file, then get the current size of the destination file and then work out the percentage that the destination is of the source and print that percentage, thus showing the progress of the copying process).

I am wanting to use this principle when converting a video with ffmpeg. Obviously, I can't use file size, since the point of using ffmepg in my case is to create a smaller destination file than the source. Instead, I am using video frames. Thus, my script calculates the total frames in the source file, then, it pipes the stdout of ffmpeg to a file (/tmp/ffmpeg), and every 10 seconds, reads what frame ffmpeg is currently on from /tmp/ffmpeg and then works out the percentage. 

Now, in theory this works, but the problem I am getting is that for some reason, it reads the output from the first line (as if I was using cat) of /tmp/ffmpeg and not the last line (when using tac) of /tmp/ffmpeg. This has got me really confused and I was wondering if it is because the file is still open as ffmpeg is writing to it, or is it a bug or what?

Here is my script:

```
#!/bin/bash
trans() {
ffmpeg -deinterlace -y -i "$1" -vcodec libx264 -level 41 -vpre normal -crf 24 -threads 0 -sn -acodec libfaac -ab 128k -ac 2 -ar 48000 -vsync 1 -async 1000 -map 0.0:0.0 -map 0.1:0.1 "$1".mkv
}



echo ffmpeg started on `date "+%m/%d/%y %l:%M:%S %p"` > ~/trans.log
# Get duration and fps
duration=( $(ffmpeg -i "$1" 2>&1 | sed -n "s/.* Duration: \([^,]*\), start: .*/\1/p") )
fps=( $(ffmpeg -i "$1" 2>&1 | sed -n "s/.*, \(.*\) tbr.*/\1/p") )

hours=( $(echo $duration | cut -d":" -f1) )
minutes=( $(echo $duration | cut -d":" -f2) )
seconds=( $(echo $duration | cut -d":" -f3) )
# Get the integer part with cut
frames=( $(echo "($hours*3600+$minutes*60+$seconds)*$fps" | bc | cut -d"." -f1) )
echo ""$1" has $frames frames, now converting" >> ~/trans.log
echo ""$1" has $frames frames, now converting" > /tmp/ffmpeg
echo ""$1" has $frames frames, now converting"
trans $1 &>> /tmp/ffmpeg &
pid=$!
echo "ffmpeg PID = $pid" >> ~/trans.log
echo "ffmpeg PID = $pid"
runtime=0
while [ -e /proc/$pid ]; do
	runtime=( $(tac /tmp/ffmpeg | grep -m 1 "frame=" | awk '{ print $2 }') )
	echo "current frame is $runtime"
	sleep 10
done

echo ffmpeg stopped on `date "+%m/%d/%y %l:%M:%S %p"` >> ~/trans.log

exit
```

So, I expect this script to currently print out every 10 seconds, the current frame that ffmpeg is on, from the /tmp/ffmpeg file. Instead,it just prints the frame value from the first frame line repeatedly.

So, whilst /tmp/ffmpeg looks like this:

```
SP.mkv has 4325 frames, now converting
FFmpeg version SVN-r23078, Copyright (c) 2000-2010 the FFmpeg developers
  built on May 10 2010 10:27:29 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.15. 2 / 50.15. 2
  libavcodec    52.67. 0 / 52.67. 0
  libavformat   52.62. 0 / 52.62. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x9dd6510]Estimating duration from bitrate, this may be inaccurate
Input #0, matroska, from 'SP.mkv':
  Duration: 00:02:53.00, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 544x576 [PAR 24:17 DAR 4:3], 25 tbr, 1k tbn, 50 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16
[libx264 @ 0x9e0feb0]using SAR=24/17
[libx264 @ 0x9e0feb0]using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x9e0feb0]profile High, level 4.1
[libx264 @ 0x9e0feb0]264 - core 93 r1542 5b86182 - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=3 wpredb=1 wpredp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=24.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.41 aq=1:1.00
Output #0, matroska, to 'SP.mkv.mkv':
  Metadata:
    encoder         : Lavf52.62.0
    Stream #0.0: Video: libx264, yuv420p, 544x576 [PAR 24:17 DAR 4:3], q=10-51, 200 kb/s, 1k tbn, 25 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=   47 fps=  0 q=29.0 size=       1kB time=1.77 bitrate=   2.7kbits/s    
frame=   82 fps= 78 q=29.0 size=      33kB time=1.32 bitrate= 202.2kbits/s    
frame=  106 fps= 68 q=29.0 size=      65kB time=2.28 bitrate= 232.0kbits/s    
frame=  126 fps= 61 q=29.0 size=      97kB time=3.08 bitrate= 256.9kbits/s    
frame=  143 fps= 56 q=29.0 size=     161kB time=3.76 bitrate= 349.9kbits/s    
frame=  156 fps= 51 q=29.0 size=     193kB time=4.28 bitrate= 368.6kbits/s    
```

My output looks like this:

```

SP.mkv has 4325 frames, now converting
ffmpeg PID = 23256
runtime is 
runtime is 47
runtime is 47
runtime is 47
etc
```

So, it is reading the first frame from the top and not the last frame from the bottom of /tmp/ffmpeg.

Any ideas what is wrong and how to fix this? I am guessing it is because ffmpeg is writing to the file so fast and constantly updating it, but if that is the problem I have no idea how to get around it.

The only other solution I can think of is to use the file size and base it on the rough factor by which my ffmpeg settings will reduce the file by, but that is a pretty naf way of doing it.....

Oh and if you got to the bottom of this post and STILL want to actually post an answer, you are a saint ;)

---

