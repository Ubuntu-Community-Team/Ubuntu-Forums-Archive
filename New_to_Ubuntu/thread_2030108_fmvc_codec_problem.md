---
title: "fmvc codec problem"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by madhav024 on 2012-07-20
Hi 
can some one help me in installing fmvc codec for ubuntu 10.10, when i play the video file i am able to play only audio but not video, so please help me out
also i have seen in some conversation that if we change the file in the path **/usr/lib/codecs**   fmcodec.DLL to fmcodec.dll it will work, but i did not see the codecs folder in the path /usr/lib/.

Regards,
Madhav

---

### Post by ron999 on 2012-07-20
> **madhav024 said:**
> installing fmvc codec for ubuntu 10.10...
... fmcodec.DLL 
Hi
That codec **fmcodec.DLL** is in the mPlayer codec package "all-20110131.tar.bz2".
The codec should work with **mPlayer/SMPlayer**, but only 32-bit Ubuntu. _**Not 64-bit**_.

If you're using 32-bit Ubuntu, this is a method how to install the package (in **usr/local/lib**).
If they're not already there in usr/local/lib.

Just one _**single**_ command to copy and paste in terminal:-

```
cd ~/ && \
sudo mkdir -pv /usr/local/lib/codecs && \
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20110131.tar.bz2 && \
tar -xf all-20110131.tar.bz2 && \
sudo cp -v all-20110131/* /usr/local/lib/codecs
```

EDIT
When you've installed all the codecs in usr/local/lib/codecs folder...
It's like you said, the codec fmcodec.DLL does need to be re-named fmcodec.dll
(That knowledge comes from here ---> [http://ubuntuforums.org/showthread.php?t=1643146]("http://ubuntuforums.org/showthread.php?t=1643146"))

---

### Post by madhav024 on 2012-08-02
Hi i have done the same thing and all the codecs got installed in the same path but i am unable to rename fmcodec.DLL to fmcodec.dll, i tried playing the video but i am unable.
There is a extra codec fmvc.exe  we need to install to play this encoded course videos, also i tried installing the codec by wine application still it is not working. 

its showing the below error even after changing the permissions

 mv: cannot move `fmcodec.DLL' to `fmcodec.dll': Permission denied

Please help me to overcome this issue.


Thanks & Regards,
Madhav.

---

### Post by madhav024 on 2012-08-02
cd /usr/local/lib/codec
mv -f  -f fmcodec.DLL fmcodec.dll

its showing below error
mv: cannot move `fmcodec.DLL' to `fmcodec.dll': Permission denied

---

### Post by ron999 on 2012-08-02
> **madhav024 said:**
> cd /usr/local/lib/codec
mv -f  -f fmcodec.DLL fmcodec.dll

its showing below error
mv: cannot move `fmcodec.DLL' to `fmcodec.dll': Permission denied

It is:-
```
cd /usr/local/lib/codecs
```

then:-

```
sudo mv fmcodec.DLL fmcodec.dll
```

---

### Post by madhav024 on 2012-08-03
Oh Thank you, i forgot to login as a root , now i will try it and i ll let you know

---

### Post by madhav024 on 2012-08-03
p, li { white-space: pre-wrap; } Hi i have renamed fmcodec.DLL to fmcodec.dll
but iam getting the below errors still i am facing same issue





log :



/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv, -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 62914907 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/madhav/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -aid 1 -subpos 100 -nocache -ss 9 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/madhav/Desktop/Linux1-1.avi
 
 MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
 
 Playing /home/madhav/Desktop/Linux1-1.avi.
 AVI file format detected.
 ID_VIDEO_ID=0
 [aviheader] Video stream found, -vid 0
 ID_AUDIO_ID=1
 [aviheader] Audio stream found, -aid 1
 VIDEO:  [FMVC]  1024x800  24bpp  14.922 fps  407.8 kbps (49.8 kbyte/s)
 ID_FILENAME=/home/madhav/Desktop/Linux1-1.avi
 ID_DEMUXER=avi
 ID_VIDEO_FORMAT=FMVC
 ID_VIDEO_BITRATE=407832
 ID_VIDEO_WIDTH=1024
 ID_VIDEO_HEIGHT=800
 ID_VIDEO_FPS=14.922
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=1
 ID_AUDIO_BITRATE=352800
 ID_AUDIO_RATE=0
 ID_AUDIO_NCH=0
 ID_START_TIME=0.00
 ID_LENGTH=1836.95
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 [***] auto-open
 Opening video filter: [screenshot]
 [***] Init
 [***] Updating font cache
 ==========================================================================
 Opening video decoder: [vfw] Win32/VfW video codecs
 ICOpen failed! unknown codec / wrong parameters?
 Loading codec DLL: 'fmcodec.dll'
 Win32 LoadLibrary failed to load: fmcodec.dll, /usr/lib/codecs/fmcodec.dll
 Can't open library fmcodec.dll
 VDecoder init failed :(
 Cannot find codec matching selected -vo and video format 0x43564D46.
 ==========================================================================
 ==========================================================================
 Opening audio decoder: [pcm] Uncompressed PCM audio decoder
 AUDIO: 22050 Hz, 1 ch, s16le, 352.8 kbit/100.00% (ratio: 44100->44100)
 ID_AUDIO_BITRATE=352800
 ID_AUDIO_RATE=22050
 ID_AUDIO_NCH=1
 Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
 ==========================================================================
 [equalizer] Limiting the number of filters to 9 due to low sample rate.
 [equalizer] Limiting the number of filters to 9 due to low sample rate.
 [equalizer] Limiting the number of filters to 9 due to low sample rate.
 AO: [pulse] 22050Hz 1ch floatle (4 bytes per sample)
 [equalizer] Limiting the number of filters to 9 due to low sample rate.
 [equalizer] Limiting the number of filters to 9 due to low sample rate.
 ID_AUDIO_CODEC=pcm
 Video: no video
 Starting playback...
 
 
 MPlayer interrupted by signal 11 in module: seek
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.
  [ This binary of MPlayer in Debian is currently compiled with
    '--enable-debug'; the debugging symbols are in the package
    'mplayer-dbg'.]

---

### Post by ron999 on 2012-08-03
> **madhav024 said:**
> ... i am facing same issue...
Hi
Check that your mPlayer plays these two files ---> [http://samples.mplayerhq.hu/V-codecs/FMVC/]("http://samples.mplayerhq.hu/V-codecs/FMVC/")

```
mplayer FMVC_6-methyl-5-hepten-2-one-CC-db.avi
```

```
mplayer FMVC_skrzyzowanie4.avi
```

---

### Post by madhav024 on 2012-08-04
[FONT=monospace]Hi i tried playing these two files but i am getting below errors


MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team

Playing skrzyzowanie4.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [FMVC]  800x520  24bpp  10.000 fps  352.1 kbps (43.0 kbyte/s)
==========================================================================
Opening video decoder: [vfw] Win32/VfW video codecs
Loading codec DLL: 'fmcodec.dll'
Win32 LoadLibrary failed to load: fmcodec.dll, /usr/lib/codecs/fmcodec.dll
Can't open library fmcodec.dll
VDecoder init failed :(
==========================================================================


Exiting... (End of file)[/FONT]

---

### Post by madhav024 on 2012-08-04
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 6-methyl-5-hepten-2-one-CC-db.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [FMVC]  664x382  24bpp  15.000 fps  1204.7 kbps (147.1 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [vfw] Win32/VfW video codecs
Loading codec DLL: 'fmcodec.dll'
Win32 LoadLibrary failed to load: fmcodec.dll, /usr/lib/codecs/fmcodec.dll
Can't open library fmcodec.dll
ICOpen failed! unknown codec / wrong parameters?
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x43564D46.
==========================================================================


Exiting... (End of file)

---

### Post by ron999 on 2012-08-04
> **madhav024 said:**
> ... Hi i tried playing these two files but i am getting below errors... 

" Win32 LoadLibrary failed to load: fmcodec.dll, **/usr/lib/codecs**/fmcodec.dll"

Hi

Those two files play OK for me.
Looks like you have a problem. :(

Your mPlayer is trying to open fmcodec.dll from folder /usr/lib/codecs.
But you've installed them in /usr/**local**/lib/codecs.
Maybe you need to move that codecs folder to /usr/lib instead of /usr/local/lib.

It is:-
```
sudo cp -r /usr/local/lib/codecs /usr/lib/codecs
```
Then:-
```
sudo rm -r /usr/local/lib/codecs
```


> @ubuntu:~$ mplayer FMVC_6-methyl-5-hepten-2-one-CC-db.avi
MPlayer SVN-r35056-4.5.2 (C) 2000-2012 MPlayer Team

Playing FMVC_6-methyl-5-hepten-2-one-CC-db.avi.
libavformat version 54.22.100 (internal)
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [FMVC]  664x382  24bpp  15.000 fps  1204.7 kbps (147.1 kbyte/s)
Load subtitles in ./
==========================================================================
Opening video decoder: [vfw] Win32/VfW video codecs
Loading codec DLL: 'fmcodec.dll'
Loaded DLL driver fmcodec.dll at 10000000
[PP] Using codec's postprocessing, max q = 9.
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 664x382 => 664x382 BGR 24-bit  [flip]
[swscaler @ 0x8ce2340]using unscaled bgr24 -> bgra special converter
Selected video codec: [foxmotion] vfm: vfw (fox motion video)
==========================================================================
Audio: no sound
Starting playback...
V:  11.5 174/174  7%  7%  0.0% 0 0

---

### Post by madhav024 on 2012-08-04
Hi do we need to install some libraries ? from the log it is showing some  shared object is not found, please guide me i am unable to find the problem.

---

### Post by madhav024 on 2012-08-05
Oh thank you i will try this

---

### Post by madhav024 on 2012-08-11
Hi, thank you for your valuable information its working fine, problem is solved.

---

