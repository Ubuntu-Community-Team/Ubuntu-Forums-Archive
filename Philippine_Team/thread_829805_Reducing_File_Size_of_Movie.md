---
title: "Reducing File Size of Movie"
date: 2008-06-15
forum: Philippine Team
---

### Post by wersdaluv on 2008-06-15
I recorded a .MOV. It's 21mins long and more than 200MB big. I am supposed to email it. The person I'm emailing it to doesn't have a fast internet connection. 

I saw [this thread]("http://ubuntuforums.org/showthread.php?p=5190120#post5190120") but I didn't learn much from it. The OP said > **avantgardaclue said:**
> Hi guys, thanks for all your help! You lot together with the guys at the avidemux forum have got me through this! My version of avidemux was, apparently, hopelessly out of date so i installed the one from getdeb and voilla, i was able to do all sorts of things!

I did the 2 pass x264 thing, raised the colours and contrast, invoked the denoise3d filter and we have a much improved much shrunk video! 

I managed to reduce the 274.4 MB video down to 44.1 MB without losing any quality 

cheeers :)

How do I do it with Avidemux or any other means?

Thanks in advance :)

---

### Post by loell on 2008-06-15
ever tried the command line tools suggested on that thread?

---

### Post by wersdaluv on 2008-06-15
> **loell said:**
> ever tried the command line tools suggested on that thread?

Ooh. Di ko sinubukan kasi sabi niya 10% lang daw niliit nung file. Sige subukan ko. Btw, ano exactly ginagawa ng code na yon at wala bang pwedeng madadagdag na arguments?

---

### Post by loell on 2008-06-15
sa mencoder parameters? yun lang ang  mga alam kung parameters eh ;)

paano namn yung ffmpeg parang ok din yun..

---

### Post by wersdaluv on 2008-06-15
Tried your code for mencoder ```
mencoder -idx '/home/user/Desktop/DCIM/100PENTX/IMGP1644.MOV' -ovc lavc -oac mp3lame -o '/home/user/Desktop/DCIM/100PENTX/output.MOV' 
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) M processor         1.50GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xcca14d4
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [mp4v]  320x240  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:7  fourcc:0x7634706D  size:320x240  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 7978 Hz, 1 ch, s16be, 127.6 kbit/100.00% (ratio: 15956->15956)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Cannot set LAME options, check bitrate/samplerate, some very low bitrates
(<32) need lower samplerates (i.e. -srate 8000).
If everything else fails, try a preset.
Exiting...

```

Pano na kaya? :(

---

### Post by wersdaluv on 2008-06-15
Pano rin pala yung ffmpeg gamitin? Nagdudugo na utak ko e. hehe

---

### Post by loell on 2008-06-15
> **wersdaluv said:**
> Pano rin pala yung ffmpeg gamitin? Nagdudugo na utak ko e. hehe

substitute mo lang ang ** input.avi** with your mov file

```
ffmpeg -y -i input.mov -pass 1 -threads auto -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions 0 -me epzs -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -an /dev/null

ffmpeg -y -i input.mov -pass 2 -threads auto -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+partp8x8+partb8x8 -me umh -subq 6 -trellis 2 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -acodec aac -ab 96k -ac 1 output.mp4
```

---

### Post by wersdaluv on 2008-06-15
Salamat, pre. Running it now. Ang tagal pala nito. hehe

---

### Post by Samhain13 on 2008-06-15
Kung gusto mo, subukan mo din yung ffmpeg2theora. OGG nga lang ang resulting format. Pero sa pagkakaintindi ko, ang OGG ay mas magaling sa optimisation so makakakuha ka ng mas magandang quality gamit ang mas mababang bitrate. Mas mababang bitrate, mas maliit na file size.

Di ko lang sigurado kung makukuha mo yung ffmpeg2theora sa Ubuntu repos. Sakin kasi, sa Medibuntu ko kinukuha.

At... hehehe... kailangan ng VLC ng kaibigan mo para mapanood yung OGG. :)

---

