---
title: "Merge avi and mp3"
date: 2008-12-28
forum: Philippine Team
---

### Post by detorresrc on 2008-12-28
Mga bro tulong naman, pano ba merge sa avi ung mp3. tnx

---

### Post by loell on 2008-12-28
avidemux?

---

### Post by Samhain13 on 2008-12-29
Hardcore? Kailangan mo ng ffmpeg:

```
$ ffmpeg -i yourvideo.avi -i youraudio.mp3 youroutputfile.avi
```

More info:

```
$ man ffmpeg
```

:D

---

