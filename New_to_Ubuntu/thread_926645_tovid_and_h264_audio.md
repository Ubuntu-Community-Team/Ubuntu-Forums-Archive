---
title: "tovid and h264 audio"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by muted1987 on 2008-09-22
when trying to encode a h264 .mp4 file to dvd i get an error for this audi input stream:

 Stream #0.1(und): Audio: mp4a / 0x6134706D, 48000 Hz, stereo


this is the error and i dont know how to sort it :-

Unsupported codec (id=86018) for input stream #0.1


any help appreciated

---

### Post by BurningFury on 2008-12-14
It looks as if you're missing a codec.
FAAD is the native AAC decoder in Linux, so see if you have it
installed.

If you still can't figure it out, then you might have to extract the
audio from your Video File.
You can do this with FFMPEG with this simple command:

> ffmpeg -i <input_file> -vn <output_file>

That will give you a complaint raw MPC audio file, from there you can
transcode it to whatever you like.

If you wish to encode it to MP4-AAC then on a terminal type:
> faac -m4 -b64 -r48000 -pLC <input_file> <output_file>

Hope that helps.

---

