---
title: "[SOLVED] bitrate in Sound Juicer"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by cjv8888 on 2008-10-05
I am using Sound Juicer to rip some CDs into mp3.
Getting a bitrate of 128 kbps.

Just wondering if it is possible to lower or increase the bitrate.

Here is the GStreamer Pipeline:

> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

Would someone in the know enlighten me?

---

### Post by falkTX on 2008-10-05
Just change "quality=6" to 10, like this:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 **vbr-quality=10** ! id3v2mux


But I recommend ogg format when ripping song, unless you have a mp3 player

EDIT: Didn't realize you want to change it and not increase it.
Well, the value can be changed from 1 to 10; 9 is fine (256Kbs, I think)

---

### Post by niteshifter on 2008-10-05
Hi,

Here's my setup in SJ for max quality, max compatibility MP3 ripping (CBR @ 320K):

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=0 bitrate=320 ! id3v2mux
```

---

### Post by cjv8888 on 2008-10-05
Thanks both.

For some reason, changing the quality did not work, the bitrate stayed at 128, but changing the line to bitrate=xxx did the trick.

---

