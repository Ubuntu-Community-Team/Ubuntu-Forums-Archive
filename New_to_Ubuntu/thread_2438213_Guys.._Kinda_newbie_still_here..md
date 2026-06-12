---
title: "Guys.. Kinda newbie still here."
date: 2020-03-07
forum: New to Ubuntu
---

### Post by xcfstarflight1 on 2020-03-07
Hi guys! I am also a musician and I was wondering.. I need to convert some .wav files to .mp3 and I need the highest and best quality.
I remember back in the days, like bladeenc stuff like that but now I don't even know the difference between encoding and decoding.
Can someone tell me what is the difference and a nice simple program that does this with zero quality loss? 

Thanks! Keep rockin ubuntu like my coffee rocks thee who takes the time to help others and step up this ubuntu OS like a  BLAST! Woa!

---

### Post by Artim on 2020-03-07
Try [this](https://www.tecrobust.com/convert-audio-files-using-sound-converter-in-ubuntu/)!

---

### Post by TheFu on 2020-03-07
mp3 is a losey audio codec.  If you don't want to lose any quality, then don't use mp3, use FLAC.
**lame** has been the go-to tool for conversion to mp3 for decades.

lame --preset extreme  <input.wav>  <output.mp3>
lame --preset insane  <input.wav>  <output.mp3>
 
You can include ID3 tags, more controls, using specific options. CBR, ABR, bitrates all under your control.

I use *--preset cbr 192 *for mp3 files, but honestly, stopped using mp3s about 5 yrs ago.  These days, ogg/vorbis and ogg/opus are considered "better" quality for the same bitrate/filesize. Obviously, which codec and container can be used for any specific target audience.  While ogg/vorbis is crazy open, no patents getting in the way, not all devices/media software seem to support it.  LOOKING AT YOU PLEX!

**ffmpeg** is also a very popular tool for conversions.  Most of the online video/audio converters are using ffmpeg underneath.  Just to convert from 1 container to another contain, losslessly, leaving the codecs inside unchanged, ffmpeg is my go-to tool.

---

### Post by xcfstarflight1 on 2020-03-07
Ok sorry about the * words xc 
noted.

---

### Post by xcfstarflight1 on 2020-03-07
Thank you, i just got the lame tool.
Now I need to add some ID3 tags like Comment, year, artist, album and genre. 
Can you help out?

---

### Post by TheFu on 2020-03-07
For tagging, it is easiest to use **easytag**.  That's a GUI with multi-select.  1 tag across all the selected files, or all tags across 1 file or some common tags across the selected files or convert the filename into tags or the tags into filenames.

---

