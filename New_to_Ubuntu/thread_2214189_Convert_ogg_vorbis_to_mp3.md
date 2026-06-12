---
title: "Convert ogg vorbis to mp3"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-03-30
I ripped some CD's using my lubuntu portable without noticing that it was ripping to OV. I wanted MP3.

The CD's are now in another city which I will not return to for a month or so and I want to be able to listen to the music in my car. OV doesn't work in the car radio, but MP3 does.

Can I somehow convert them to MP3 without losing all semblance of quality? And if so, how please?

TIA

---

### Post by deadflowr on 2014-03-30
I think audacity can do that.
Though that one is probably overtop for this purpose.

Another would be soundconverter, which in a gnome app.
Should work with lubuntu as well.

There probably a super simple ffmpeg command line solution which you could also try.
Again, though, I don't off the top know it/remember it.

Those are a couple I can think of off the top.

---

### Post by monkeybrain20122 on 2014-03-30
ffmpeg can do that.

```
ffmpeg -i audiofile.ogg -acodec limpmp3lame audiofile.mp3
```

But why do you want to do that? You are converting a lossy format to another lossy format and ogg has better quality than mp3 anyway. I rip my cds in flac.

---

### Post by vasa1 on 2014-03-30
> **monkeybrain20122 said:**
> ..
But why do you want to do that? You are converting a lossy format to another lossy format and ogg has better quality than mp3 anyway. ...
His car radio needs mp3 (first post).

---

### Post by Odyssey1942 on 2014-03-30
```
The CD's are now in another city which I will not return to for a month or so and I want to be able to listen to the music in my car. OV doesn't work in the car radio, but MP3 does.
```

This is a "temporary" fix.

Am I missing something obvious here?

---

### Post by deadflowr on 2014-03-30
> **Odyssey1942 said:**
> ```
The CD's are now in another city which I will not return to for a month or so and I want to be able to listen to the music in my car. OV doesn't work in the car radio, but MP3 does.
```

This is a "temporary" fix.

Am I missing something obvious here?

I don't think you're missing anything.
Car stereo seems to be mp3 compatible but not ogg compatible.
If something isn't compatible to play a certain format, then it won't.

However, that said, it might be possible that even though it can't play ogg files, it might be able to play flac files.
(Maybe possible, but no guarantee)

But for what's it is worth, the above mentioned soundconverter can easily convert whole folders at once, so I'll stick with that recommendation.
(You have to go to preferences first to set formats and stuff like that, easypeasy though)

---

### Post by vasa1 on 2014-03-30
> **Odyssey1942 said:**
> ...
This is a "temporary" fix.

Am I missing something obvious here?
Two suggestions have been offered: Audacity and ffmpeg. If you have a "full" install of Lubuntu (restricted extras installed), you shouldn't have a problem. Where are you getting stuck?

---

### Post by andrew.46 on 2014-03-31
> **monkeybrain20122 said:**
> ffmpeg can do that.

```
ffmpeg -i audiofile.ogg -acodec limpmp3lame audiofile.mp3
```


Mind you the *default* bitrate is 128.0kbits/s which may or may not be appropriate...

---

### Post by Christmas on 2014-03-31
You can also do it with **oggdec** and **lame**, however converting between lossy audio files is not recommended. But anyway, you can install **vorbis-tools** and **lame** (e.g. **sudo apt-get install vorbis-tools lame**) and then convert them like this:
```
oggdec song.ogg
lame -b 128 song.wav
```
The first command will convert the Ogg into a resulting WAV file, and then lame will convert the WAV to MP3.

You can also use wildcards for all the Ogg files, like **oggdec *.ogg**. However, I think lame doesn't support wildcards (I may be wrong though). Also, replace 128 with the desired bitrate, and keep in mind the resulting MP3 files will have a bit lower quality than the Ogg ones.

---

### Post by Odyssey1942 on 2014-03-31
Vasa, a very cogent question. I think maybe I haven't installed the restricted extras. How does one do that? (If I can rip to MP3 in future, I want to be able to do that.)

Thanks all for the program recommendations. Will also try Flac to see if the car radio will play that.

---

### Post by sudodus on 2014-03-31
```
sudo apt-get install lubuntu-restricted-extras
```

---

### Post by newb85 on 2014-03-31
One could also install lubuntu-restricted-extras from the Software Center.

---

### Post by SeijiSensei on 2014-03-31
I suspect the radio is unlikely to support FLAC.  WAV might be a possibility though.

```
ffmpeg -i audiofile.ogg -acodec limpmp3lame audiofile.mp3
```
MP3 may be a "limp" technology, but the correct codec is "libmp3lame:"
```
ffmpeg -i audiofile.ogg -acodec libmp3lame audiofile.mp3
```

---

### Post by Odyssey1942 on 2014-04-01
Will be at that computer again on Friday and will install the restricted extras, and have a go at the conversion (though my expectations for quality results, based on the comments, are modest.)

Thanks all

---

### Post by FakeOutdoorsman on 2014-04-02
If I recall correctly **libavcodec-extra-53** is all that is required to enable MP3 encoding in the so-called "ffmpeg" if you don't want all of the other stuff from ***ubuntu-restricted-extras**.
Or just [download a recent static build of ffmpeg](https://ffmpeg.org/download.html#LinuxBuilds). The package in the repo is ancient anyway.

---

