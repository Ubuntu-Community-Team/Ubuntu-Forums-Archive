---
title: "ffmpeg bash script: wav extraction from videos"
date: 2016-05-15
forum: Programming Talk
---

### Post by jonesints on 2016-05-15
After hunting for hours through forums, I'm stuck from just achieving basics with ffmpeg with my limited bash knowledge.

What I'm trying to achieve:

6TB of video files of different codecs on my headless server (of mainly wrappers .mov & mp4) in several directories. I would like to extract the audio from them as .wav, and save the audio in a separate location KEEPING the folder structures in this new location. (I don't mind if re-encoding audio but if just extracting the right audio codec is faster, and less processing, then better!)

```


#!/bin/bash
for filename in *.mp4; 
do
    stub="${filename%.*}" 
   /usr/local/bin/ffmpeg -i "${stub}.mp4" -vn -acodec copy "Someotherpath/FolderStructureRecreated/${stub}.wav"

sleep 0.1

done
```

Would I need to use "find" instead, if names are more complex with characters/spaces?

---

### Post by steeldriver on 2016-05-15
Using `find` isn't really about filename complexity - it's about file location. It will search through directories recursively, whereas the shell glob *.mp4 will only find files in the current directory.

---

### Post by FakeOutdoorsman on 2016-05-16
MP4 does not support PCM audio. You're attempting to [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) the existing audio from the MP4 input into WAV which will result in an invalid file. You should re-encode instead.

---

