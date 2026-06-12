---
title: "Help a noob: Sound suddenly broken 10.04 with USB audio"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by SiliconS on 2012-04-18
I've got an HP Proliant microserver onto which I've installed Lucid.  There's no on-board sound so I bought a USB audio adapter that uses the  same chipset as the ThinkPenguin one recommended as out-of-the-box  compatible:  [https://www.thinkpenguin.com/gnu-linux/penguin-usb-20-external-usb-sound-card-gnulinux](https://www.thinkpenguin.com/gnu-linux/penguin-usb-20-external-usb-sound-card-gnulinux)

All was good for several weeks. Until I tried to change the stereo  balance in the Sound Preferences dialog. That killed the sound. Dead.  Apps don't seem to be reporting any kind of problem but no sound comes  out of the headphone jack in the audio adapter.

This machine doesn't have much installed, so the only app whose log file  I know how to access is Subsonic, and this is what it says when I try  to play a track (does it help?):
```
[4/18/12 12:50:56 PM BST]     DEBUG    TranscodeInputStream     Starting transcoder: [/var/subsonic/transcode/ffmpeg] [-ss] [0] [-i]  [/media/Music/The Zutons/01-zuton_fever_192_lame_cbr.mp3] [-v] [0] [-f]  [au] [-]
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) ffmpeg version N-31780-gd5d74cf,  Copyright (c) 2000-2011 the FFmpeg developers
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) built on Aug 9 2011 14:18:27 with gcc  4.5.2
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) configuration: --disable-ffplay  --disable-ffprobe --disable-ffserver --enable-gpl --enable-nonfree  --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame  --enable-libvpx --enable-libtheora --enable-libvorbis --enable-libx264  --enable-libxvid --enable-zlib --enable-libopencore-amrnb  --enable-libopencore-amrwb --enable-libvpx --enable-version3  --enable-bzlib --enable-static --disable-shared --extra-libs=-static  --extra-cflags=--static
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) libavutil 51. 11. 1 / 51. 11. 1
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) libavcodec 53. 9. 1 / 53. 9. 1
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) libavformat 53. 6. 0 / 53. 6. 0
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) libavdevice 53. 2. 0 / 53. 2. 0
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) libavfilter 2. 28. 1 / 2. 28. 1
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) libswscale 2. 0. 0 / 2. 0. 0
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) libpostproc 51. 2. 0 / 51. 2. 0
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) [mp3 @ 0x92f6be0] max_analyze_duration  5000000 reached at 5015510
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) Input #0, mp3, from '/media/Music/The  Zutons/01-zuton_fever_192_lame_cbr.mp3':
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) Metadata:
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) title : Zuton Fever
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) artist : The Zutons
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) album : Who Killed The Zutons
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) date : 2004
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) Duration: 00:03:08.29, start: 0.000000,  bitrate: 192 kb/s
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) Stream #0.0: Audio: mp3, 44100 Hz,  stereo, s16, 192 kb/s
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) Output #0, au, to 'pipe:':
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) Metadata:
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) title : Zuton Fever
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) artist : The Zutons
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) album : Who Killed The Zutons
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) date : 2004
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) encoder : Lavf53.6.0
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) Stream #0.0: Audio: pcm_s16be, 44100  Hz, stereo, s16, 1411 kb/s
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) Stream mapping:
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread    (/var/subsonic/transcode/ffmpeg) Stream #0.0 -> #0.0
[4/18/12 12:50:56 PM BST]     DEBUG    InputStreamReaderThread     (/var/subsonic/transcode/ffmpeg) Press [q] to stop, [?] for help
[4/18/12 12:50:56 PM BST]     DEBUG    JukeboxService    Opened line com.sun.media.sound.DirectAudioDevice$DirectSDL@93c911
[4/18/12 12:50:56 PM BST]     INFO    JukeboxService    stormjukebox  starting jukebox for "The Zutons/01-zuton_fever_192_lame_cbr.mp3"

```I'm a complete noob when it comes to diagnosing hardware issues on  Linux, so if any kind soul would be willing to guide me through that  process, telling me which shell commands to run for the diagnosis and  remedy, I'd be very grateful. I've tried searching already but I haven't  found anybody with the same problem and the same hardware.

---

### Post by dzponce11 on 2012-04-18
Hi!
Has this problem happened before? If not, it's maybe because you're using Lynx? Not sure if that's it, but i'm sort of a noob when it comes to audio problems. :/. I'm really sorry.

~~~~dzponce11

---

### Post by SiliconS on 2012-04-19
> **dzponce11 said:**
> Has this problem happened before? If not, it's maybe because you're using Lynx?
No, as I say, the sound has been working fine with the USB audio adapter.

It would be surprising if I had to re-install Ubuntu simply to fix this problem, especially if the problem could arise again without warning.

---

### Post by SiliconS on 2012-04-20
Shameless bump: Help pleeeeease :)

---

