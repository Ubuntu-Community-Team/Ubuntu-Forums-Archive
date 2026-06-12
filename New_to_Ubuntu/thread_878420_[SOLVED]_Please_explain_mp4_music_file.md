---
title: "[SOLVED] Please explain mp4 music file"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by paker on 2008-08-02
I have a music file, say, Brahms-Piano.mp4. It has the movie film icon. Double click. Totem Movie Player pops and plays the music. No video. Can an mp4 file be empty of video? 

Right click > Properties.

Type: MPEG-4 video
Size: 39.3 MB
 
Click on AUDIO tab

Duration: 21 minutes
Codec: MPEG-4 AAC
Channels: Stereo
Sample Rate: 44100 hz

I tried Audacity. It cannot import AAC files. What program will convert MPEG-4 AAC to mp3? My goal is to put it on my non-Apple mp3 player. Thanks.

---

### Post by talsemgeest on 2008-08-02
You might want to give Avidemux a go. It is primarily a video editor/converter, but it can also save/convert just the audio, and should be able to save the audio to an mp3.

---

### Post by eightmillion on 2008-08-02
paker, you could use this from the command line:
> ffmpeg -i Brahms-Piano.mp4 -acodec mp3 -ac 2 -ab 128 Brahms-Piano.mp3

---

### Post by paker on 2008-08-03
Thanks. Avidemux could not open MPEG-4 AAC. But I can use Avidemux for video editing in the future. Thanks.

Thanks for the command line coding.

I tried Sound Converter. It worked well. One thing I learned from this exercise is that converting from one lossy format to another is not ideal. I set for vbr ~200 kbps mp3, but the best I could get was ~150 kbps. Original AAC file was about the ~250 mp3 size. I will try AAC > FLAC > mp3.  If anyone has any comment on converting one lossy format to another, I would like to hear. Thanks.

---

### Post by FakeOutdoorsman on 2008-08-03
> **eightmillion said:**
> paker, you could use this from the command line:
ffmpeg -i Brahms-Piano.mp4 -acodec mp3 -ac 2 -ab 128 Brahms-Piano.mp3
ffmpeg from the Ubuntu repository has not been compiled to support [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats") such as mp3.  You can use ffmpeg from a third-party repository such as [Medibuntu]("http://www.medibuntu.org") or [compile ffmpeg]("http://ubuntuforums.org/showthread.php?t=786095") yourself.  Also, some options have changed names between various ffmpeg releases, so if you're using Medibuntu's ffmpeg you will need to add a "k" to the bitrate:
```
ffmpeg -i Brahms-Piano.mp4 -acodec mp3 -ac 2 -ab 128k Brahms-Piano.mp3
```
[QUOTE=paker]Can an mp4 file be empty of video?[/QUOTE]
Yes, since MP4 is a container format it can contain audio, video, and/or subtitle data.

---

### Post by paker on 2008-08-05
Thanks for the explanation for mp4 format.
I decided not to convert mp4 AAC to mp3, not a good idea.

---

