---
title: "extract mp3 from avi"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by paker on 2013-06-16
How can I extract audio (mp3) from video (avi)? Audio is already in mp3. Avidemux doesn't seem to let me save just the audio without conversion. Thanks.

---

### Post by deadflowr on 2013-06-16
I always just use audacity.
Open the file and it automagically converts the audio to mp3, or some other audio.
Then you can export it as an mp3 or flac or whatever you want.

---

### Post by paker on 2013-06-16
Thanks. Will follow the instruction.

---

### Post by HiImTye on 2013-06-17
```
sudo apt-get install ffmpeg
ffmpeg -i /path/to/infile.avi /path/to/outfile.mp3
```
if you have to cut it, use```
sudo apt-get install mencoder ffmpeg
mencoder /path/to/infile.avi -ss **[COLOR=#008000]1:03[/COLOR]** -oac copy -ovc copy -o /path/to/outfile1.avi
mencoder /path/to/outfile1.avi -endpos [COLOR=#ffd700]**:43**[/COLOR] -ovc copy -oac copy -o /path/to/outfile2.avi
ffmpeg -i /path/to/outfile2.avi /path/to/outfile.mp3
```where **[COLOR=#008000]1:03[/COLOR]** is the **[COLOR=#008000]start time[/COLOR]**, and **[COLOR=#ffd700]:43[/COLOR]** is the **[COLOR=#ffd700]duration[/COLOR]**.

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by FakeOutdoorsman on 2013-06-17
Since you already know what your input audio format is with ffmpeg you can [stream copy](https://ffmpeg.org/ffmpeg.html#Stream-copy) the audio without re-encoding, therefore being fast and will not lose quality:
```
ffmpeg -i input -codec:a copy output.mp3
```

If you want to create a segment you could just use ffmpeg:
```
ffmpeg -i input -ss 00:01:00 -t 5 -codec:a copy output.mp3
```
"-ss" is the offset time and "-t" is the duration, so it would skip the first minute and create an output with a duration of 5 seconds.

If you just want to find out more about the input ffmpeg will give info:
```
ffmpeg -i input
```

---

### Post by HiImTye on 2013-06-17
> **FakeOutdoorsman said:**
> If you want to create a segment you could just use ffmpeg:
```
ffmpeg -i input -ss 00:01:00 -t 5 -codec:a copy output.mp3
```
"-ss" is the offset time and "-t" is the duration, so it would skip the first minute and create an output with a duration of 5 seconds
even I learn something here sometimes :D
[quote=mencoder]I'm useful for splitting clips![/quote]
[quote=ffmpeg]I can do that.[/quote]
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by coffeecat on 2013-06-17
> **paker said:**
> Avidemux doesn't seem to let me save just the audio without conversion.

Are you sure about that? Opening an avi with mp3 audio in Avidemux, I was able to save the mp3 soundtrack from the Avidemux Audio menu -> Save. It took a few seconds only and I ended up with a playable mp3 file.

---

### Post by palmgrower on 2013-10-10
Thanks. I was able to solve the problem.

---

