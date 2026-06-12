---
title: "Strange Bash"
date: 2007-07-29
forum: Programming Talk
---

### Post by hyper_ch on 2007-07-29
Hiho

I'm on the verge of converting all my DVDs to MPEG4/OGG so that I have them always on my notebook. I stumbled accross this thread here [http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635) and have tried to make a script that will sort of automate most of it.

Here's my script:

```

#!/bin/bash

while read EP
do

: <<COMM

	# Umount existing image
	umount /media/cdrom0

	# Mount image
	mount -t iso9660 -o loop /media/hda1/B5/$EP.iso /media/cdrom0

	# Rip files
	nice -n20 mplayer -dvd-device /media/cdrom0 dvd://1 -v -dumpstream -dumpfile $EP.vob
	nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
		-nosound -ovc frameno -o /dev/null -slang en -vobsubout $EP.en
	nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
		-nosound -ovc frameno -o /dev/null -slang de -vobsubout $EP.de
COMM

	echo "nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null"
	nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null

: <<COMMENT

	nice -n20 normalize-audio $EP.wav
	nice -n20 oggenc -q5 $EP.wav


	# First pass
	nice -n20 mencoder -v \
		$EP.vob \
#		-vf crop=720:576:0:0,harddup \
		-ovc x264 -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000 \
		-oac copy \
		-of rawvideo \
		-o title.264

	# Second pass
	nice -n20 mencoder -v \
		$EP.vob \
#		-vf crop=720:576:0:0,harddup \
		-ovc x264 -x264encopts \
		subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \
		-oac copy \
		-of rawvideo \
		-o title.264
	
	MP4Box -add title.264 $EP.mp4
	
	rm $EP.vob
	rm $EP.wav
	rm title.264

COMMENT

	chown hyper.hyper *

      	echo "$EP done"

done < "list.txt"

```
Most of it is currently commented out because I'm failing at one point. The problem is the ripping of to the .wav file. That won't work.
```

	echo "nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null"
	nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null

```
I get this output here:
```

nice -n20 mplayer S02E01.vob -ao pcm:file=S02E01.wav -vc dummy -aid 128 -vo null
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm)   2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing S02E01.vob.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
==========================================================================
Forced video codec: dummy
Cannot find codec matching selected -vo and video format 0x10000002.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO PCM] File: S02E01.wav (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
[Mixer] No hardware mixing, inserting volume filter.
Volume: 97 %


Exiting... (End of file)

```
There are two strange things:
(1) It says no hwad ware mixing
(2) It doesn't continue to loop through the script

When I invoke that code from the terminal
```

nice -n20 mplayer S02E01.vob -ao pcm:file=S02E01.wav -vc dummy -aid 128 -vo null

```
It works fine and I get this output:
```

MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm)   2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing S02E01.vob.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
==========================================================================
Forced video codec: dummy
Cannot find codec matching selected -vo and video format 0x10000002.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO PCM] File: S02E01.wav (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  64.9 (01:04.9) of 2517.7 (41:57.6)  1.5% 

MPlayer interrupted by signal 2 in module: decode_audio

```
(Well, until I interrupt it...)

To make things even more strange, I have written another small script:
```

#!/bin/bash -x

EP=S02E01

echo "nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null"
nice -n20 mplayer $EP.vob -ao pcm:fast:file=$EP.wav -vc dummy -aid 128 -vo null

echo "Done"

```
That also runs just fine... so I am wondering why isn't it running fine in the loop?

---

### Post by SeanHodges on 2007-07-29
You might have some hidden characters in the variable returned by your "while read" line, which will not be shown in the terminal but are being sent to mplayer. Most likely is a carriage return at the end.

I haven't had much time to look into this, but one possible solution is to add this line immediately after your "do":

```
$EP=${$EP%% *}
```

I've read that this trims spaces from a variable, it might also do the same for hidden characters...

If that doesn't work, I think hidden characters are most likely your problem, and that you need to trim them off somehow.

I will put this to the test tomorrow, if you don't post back before then.

Regards,

Sean

---

