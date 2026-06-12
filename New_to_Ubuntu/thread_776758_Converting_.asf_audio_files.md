---
title: "Converting .asf audio files"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by FleetAdmiral74 on 2008-04-30
I'm looking to convert a .asf file (some audio book format I think) to a mp3. However, ffmpeg does not seem to support this, a least not out of the box. 

Pointers?

---

### Post by mc4man on 2008-05-01
Never done it but i think you need to convert to .wav first, then mp3

---

### Post by spiderbatdad on 2008-05-01
```
   ffmpeg -r 1 -i file_name.asf -r 24 file_name.avi

```
??

---

### Post by mc4man on 2008-05-01
If it's an audio file I'd go (assuming in home directory)
```
mplayer -vc null -vo null -aid 1 -ao pcm:waveheader:file=<whatever>.wav <whatever>.wma

``` then ```
lame -b 192 -h <whatever>.wav <whatever>.mp3
```
either changing comm. to .asf or renaming source file to .wma
-b 192 can be adjusted to suit (default is 128)
-aid 1 - may be different, mplayer will tell you

---

### Post by FleetAdmiral74 on 2008-05-01
tldr: Codec does not seem to be installed, as vlc/mplayer can't play the file at all.

> **spiderbatdad said:**
> ffmpeg -r 1 -i file_name.asf -r 24 file_name.avi??

```
ed@linuxbox:~$ ffmpeg -r 1 -i /home/ed/Desktop/Under\ the\ Banner\ of\ Heaven\ \(Unabridged\)_acelp16_thompsonjp28.asf -r 24 /home/ed/Desktop/Under.avi
------------
Unsupported codec (id=0) for input stream #0.0

```

> If it's an audio file I'd go (assuming in home directory)

```
ed@linuxbox:~$ mplayer -vc null -vo null -aid 1 -ao pcm:waveheader: /home/ed/Desktop/Under\ the\ Banner\ of\ Heaven\ \(Unabridged\)_acelp16_thompsonjp28.asf /home/ed/Desktop/Under.wav
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 12, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/ed/Desktop/Under the Banner of Heaven (Unabridged)_acelp16_thompsonjp28.asf.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: Under the Banner of Heaven: A Story of Violent Faith (Unabridged)
 author: Jon Krakauer
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: acelpdec.ax, /usr/lib/win32/acelpdec.ax, /usr/local/lib/win32/acelpdec.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=acelpdec.ax, r=0x0)
ERROR: Could not open required DirectShow codec acelpdec.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x130.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Playing /home/ed/Desktop/Under.wav.
File not found: '/home/ed/Desktop/Under.wav'
Failed to open /home/ed/Desktop/Under.wav.

```

---

### Post by mc4man on 2008-05-01
Is this an audio only file ?
Do you have w32codecs installed ?
The mplayer command your using is slightly wrong but above is more important for the moment
Edit; my fault for using <whatever> whatever = filename only
there is no space in pcm:waveheader:newfilename.wav
it's much easier to work from home directory instead of desktop - no file paths needed. The only issue I initially had was using orig. filename with spaces and capitals, once renamed worked fine (1st. time I tried this, could be worked out i think )
.wma and .asf are interchangeable with audio only, .wmv and .asf are interchangeable for video
here's specific example - orig. file was 13 Bold as Love.wma - renamed to boldaslove.wma  (in home directory)
```
doug@doug-desktop:~$ mplayer -vc null -vo null -aid 1 -ao pcm:waveheader:file=boldaslove.wav boldaslove.wma
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
<clipped >
Playing boldaslove.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: Bold as Love
 author: Jimi Hendrix Experience
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
GetOutput r=0x0   size:16384  align:1
StreamCount r=0x0  1  1
AUDIO: 44100 Hz, 2 ch, s16le, 954.6 kbit/67.65% (ratio: 119331->176400)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
[AO PCM] File: boldaslove.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 254.2 (04:14.1) of 255.0 (04:15.0)  4.2% 

Exiting... (End of file)
```
for lame ck. lame --help and or lame --preset help for parameters

---

