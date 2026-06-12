---
title: "[SOLVED] Can Sound Converter convert .mpg to mp3?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by swarup on 2008-07-20
I have been using Sound Converter for a long time to convert .wav files to mp3 format. But today I had a .mpg file which I needed to convert to mp3 format. So I opened Sound Converter, browsed to my .mpg file and brought it into Sound converter. Selected the destination format as mp3, and gave the command to execute. It accepted the command, but it has been going on for quite some time, and the "time left" counter is going UP instead of DOWN. Now it says there are 68,000 hours left, and going up continuously. So obviously something isn't right. Could you give me some insight? Thanks!

---

### Post by asmoore82 on 2008-07-20
I'll take a stab at it but this is Hack-y ...

install `mplayer` via your preferred method (apt-get, Synaptic, etc.)

run this command in a Terminal "Applications -> Accessories -> Terminal"
(click and Drag the *.mpg file into the terminal to get the filename perfect)
```
mplayer -vc dummy -vo null -ao pcm:fast *</Path/to/media-file.mpg>*
```
 
This will create an "audiodump.wav" file in your home folder and you can take it from there!

---

### Post by swarup on 2008-07-20
Thanks--I've got mplayer already, and will give it a shot now. 

The odd thing though, is that Sound Converter is supposed to be able to accept .mpg files as I understand. So why shouldn't it work directly in Sound Converter?

---

### Post by asmoore82 on 2008-07-20
> **swarup said:**
> Thanks--I've got mplayer already, and will give it a shot now. 

The odd thing though, is that Sound Converter is supposed to be able to accept .mpg files as I understand. So why shouldn't it work directly in Sound Converter?

All sorts of things can be off-tilt in high level MultiMedia encapsulation formats ... 
`mplayer` can be helpful what that too, with `-v` it will be painfully specific about what's up with the file.

---

### Post by swarup on 2008-07-20
Here is the terminal output:

```
krpa@krpa-desktop:~$ mplayer -vc dummy -vo null -ao pcm:fast </home/krpa/VCD/avseq02.mpg>
bash: syntax error near unexpected token `newline'
krpa@krpa-desktop:~$ 
```

---

### Post by asmoore82 on 2008-07-20
> **swarup said:**
> Here is the terminal output:

```
krpa@krpa-desktop:~$ mplayer -vc dummy -vo null -ao pcm:fast </home/krpa/VCD/avseq02.mpg>
bash: syntax error near unexpected token `newline'
krpa@krpa-desktop:~$ 
```

sorry, you don't actually need to type the '<' and '>'
I just use them to illustrate that it was a "virtual" filename :KS

---

### Post by swarup on 2008-07-20
Hey, great! It worked. :)
Very impressive.

One question: The sound file is larger (277 MB) than the video file from which it was extracted (274 MB). Isn't that a bit odd? I am going to create a cd of around 60 such mp3 files created through this process, so I'd like to make sure the files aren't any larger than they need to be.

Here is the terminal output from the session, in case it may be helpful. Also, there is one line in the output which suggests a faster way to do it.
```

krpa@krpa-desktop:~$ mplayer -vc dummy -vo null -ao pcm:fast /home/krpa/VCD/avseq02.mpg
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/krpa/.mplayer/config
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/krpa/VCD/avseq02.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1150.0 kbps (143.8 kbyte/s)
==========================================================================
Forced video codec: dummy
Cannot find codec matching selected -vo and video format 0x10000001.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
[AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
Cannot sync MAD frame 1647.7 (27:27.7)  2.0% 
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame 1647.7 (27:27.7)  2.0% 
A:1650.7 (27:30.6) of 1647.7 (27:27.7)  2.0% 

Exiting... (End of file)
krpa@krpa-desktop:~$ 
```

---

### Post by asmoore82 on 2008-07-27
Yes, WAV files are uncompressed audio so they will be quite large;
you just need them as a stop-gap to make the mp3 files
so you can delete them ASAP.

---

### Post by swarup on 2008-07-27
But my question is that the sound file was *contained inside *the video file. And video files are much larger than audio files. So how could the .wav file--which is only sound--be larger than the file which it was inside of and which is itself a video file? This doesn't make sense, does it?

---

