---
title: "Which tools for debugging MP3 problems?"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by Raphicerus on 2012-10-21
For a while I have been using get-iplayer to listen to radio on an mp3 player. All was fine until I tried the audios on my Sansa Fuze+. They play, but the fast forward doesn't work. (It scrolls to +1 minute and sticks).

"Properties" doesn't give me much detail about encoding, format and so on. What should I install to dig down into the details?

---

### Post by Cheesemill on 2012-10-21
You can use mplayer:
```
mplayer -identify file.mp3
```Take a look for the ID_SEEKABLE property.
```
rob@arch:~/Music/Blur - Discography/Blur - Leisure$ mplayer -identify 06_Sing.mp3 
MPlayer SVN-r35014-4.7.1 (C) 2000-2012 MPlayer Team
195 audio & 404 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 06_Sing.mp3.
libavformat version 54.15.100 (internal)
ID_AUDIO_ID=0
Audio only file format detected.
Clip info:
 Title: Sing
ID_CLIP_INFO_NAME0=Title
ID_CLIP_INFO_VALUE0=Sing
 Artist: Blur
ID_CLIP_INFO_NAME1=Artist
ID_CLIP_INFO_VALUE1=Blur
 Album: Leisure
ID_CLIP_INFO_NAME2=Album
ID_CLIP_INFO_VALUE2=Leisure
 Year: 1991
ID_CLIP_INFO_NAME3=Year
ID_CLIP_INFO_VALUE3=1991
 Comment:  YEAR: 1991

ID_CLIP_INFO_NAME4=Comment
ID_CLIP_INFO_VALUE4= YEAR: 1991

 Track: 6
ID_CLIP_INFO_NAME5=Track
ID_CLIP_INFO_VALUE5=6
 Genre: Unknown
ID_CLIP_INFO_NAME6=Genre
ID_CLIP_INFO_VALUE6=Unknown
ID_CLIP_INFO_N=7
Load subtitles in ./
ID_FILENAME=06_Sing.mp3
ID_DEMUXER=audio
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=0
ID_START_TIME=0.00
ID_LENGTH=360.00
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Opening audio decoder: [mpg123] MPEG 1.0/2.0/2.5 layers I, II, III
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mpg123] afm: mpg123 (MPEG 1.0/2.0/2.5 layers I, II, III)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mpg123
Video: no video
Starting playback...
A:  29.5 (29.5) of 360.0 (06:00.0)  0.6% 


MPlayer interrupted by signal 2 in module: play_audio
ID_SIGNAL=2
A:  29.5 (29.5) of 360.0 (06:00.0)  0.6% 

Exiting... (Quit)
ID_EXIT=QUIT
```

---

### Post by Raphicerus on 2012-10-21
Thanks for that, Cheesemill, I didn't know about mplayer.

I got
```

mplayer -identify Daphne_Du_Maurier_The_Birds_Episode_3.mp3
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Daphne_Du_Maurier_The_Birds_Episode_3.mp3.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
ID_AUDIO_ID=0
Audio only file format detected.
Clip info:
 Title: Drama,Thriller, Episode 3
ID_CLIP_INFO_NAME0=Title
ID_CLIP_INFO_VALUE0=Drama,Thriller, Episode 3
 Artist: BBC Radio 4 Extra
ID_CLIP_INFO_NAME1=Artist
ID_CLIP_INFO_VALUE1=BBC Radio 4 Extra
 Album: Daphne Du Maurier - The Birds
ID_CLIP_INFO_NAME2=Album
ID_CLIP_INFO_VALUE2=Daphne Du Maurier - The Birds
 Year: 2008
ID_CLIP_INFO_NAME3=Year
ID_CLIP_INFO_VALUE3=2008
 Comment: Will the Triggs be able to h
ID_CLIP_INFO_NAME4=Comment
ID_CLIP_INFO_VALUE4=Will the Triggs be able to h
 Track: 3
ID_CLIP_INFO_NAME5=Track
ID_CLIP_INFO_VALUE5=3
 Genre: Unknown
ID_CLIP_INFO_NAME6=Genre
ID_CLIP_INFO_VALUE6=Unknown
ID_CLIP_INFO_N=7
Load subtitles in ./
ID_FILENAME=Daphne_Du_Maurier_The_Birds_Episode_3.mp3
ID_DEMUXER=audio
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=0
ID_START_TIME=0.00
ID_LENGTH=2160.00
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 44100 Hz, 2 ch, floatle, 128.0 kbit/4.54% (ratio: 16000->352800)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffmp3float
Video: no video
Starting playback...
A:  10.5 (10.4) of 2160.0 (36:00.0)  0.4% 


```

It got ID_SEEKABLE. Nothing jumps out as obviously bad. I'll compare it side-by-side with one that works...

---

### Post by Raphicerus on 2012-10-25
I used LAME to convert the mp3s to CBR 128 kbit simple stereo, and that seemed to fix it. I still don't really understand what the problem was, but the workaround is good enough!

Will mark as solved.

Thanks for the suggestions.

---

