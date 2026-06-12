---
title: "Ripping film apart frame by frame"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2008-08-21
Anyone know how I can take a movie (Night of the Living Dead) and make each frame a jpg image without using the print screen key

---

### Post by brian_p on 2008-08-22
> **linuxguymarshall said:**
> Anyone know how I can take a movie (Night of the Living Dead) and make each frame a jpg image without using the print screen key

Something along the lines of:

```
ffmpeg -r 25 -s 480x360 output%05d.jpg -i movie.mpg
```

---

### Post by FakeOutdoorsman on 2008-08-22
FFmpeg FAQ 3.3 [How do I encode movie to single pictures?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC15")
> Use:
ffmpeg -i movie.mpg movie%d.jpg

The `movie.mpg' used as input will be converted to `movie1.jpg', `movie2.jpg', etc...

Instead of relying on file format self-recognition, you may also use

`-vcodec ppm'
`-vcodec png'
`-vcodec mjpeg'

to force the encoding.

Applying that to the previous example:
ffmpeg -i movie.mpg -f image2 -vcodec mjpeg menu%d.jpg

Beware that there is no "jpeg" codec. Use "mjpeg" instead. 

---

