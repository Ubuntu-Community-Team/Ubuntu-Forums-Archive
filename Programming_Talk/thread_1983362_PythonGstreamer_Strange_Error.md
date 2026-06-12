---
title: "Python/Gstreamer: Strange Error"
date: 2012-05-20
forum: Programming Talk
---

### Post by Nebelhom on 2012-05-20
Hi folks,

I posted this message already on [stackoverflow]("http://stackoverflow.com/questions/10669640/strange-python-wxpython-gstreamer-error"), but unfortunately noone answered, so I am trying it here, because there seems to be a fair amount of Gstreamer aficionados around here.
I apologise if you read this before. Thank you for any input.

------------------------------------------------------------------------

I've come across a really strange error which I am trying to narrow down to a certain point. Basically, I am writing a music player. On starting it, it just lists all songs in the chosen folder (and its subfolders) and the song length in a separate column. During the initialisation process Python and its libraries, wxPython and Gstreamer are used.

Everything works fine when using a small amount of songs (I've tried up to 20), but when using my entire music folder, I receive the following errors.

```
No accelerated IMDCT transform found
No accelerated IMDCT transform found
0:00:43.468750000  3512   03A52E68 ERROR                 ffmpeg .:0:: big_values too big
0:00:43.468750000  3512   03A52E68 ERROR                 ffmpeg .:0:: invalid new backstep -145
0:00:43.500000000  3512   03A52E68 ERROR                 ffmpeg .:0:: invalid block type
0:00:43.500000000  3512   03A52E68 ERROR                 ffmpeg .:0:: invalid block type
0:00:43.500000000  3512   03A52E68 ERROR                 ffmpeg .:0:: big_values too big
0:00:43.500000000  3512   03A52E68 ERROR                 ffmpeg .:0:: invalid new backstep -289
0:00:43.500000000  3512   03A52E68 ERROR                 ffmpeg .:0:: invalid block type
0:00:43.515625000  3512   03A52E68 ERROR                 ffmpeg .:0:: invalid block type
0:00:43.515625000  3512   03A52E68 ERROR                 ffmpeg .:0:: big_values too big
0:00:43.515625000  3512   03A52E68 ERROR                 ffmpeg .:0:: invalid new backstep -137
```

I would assume, it's got something to do with gstreamer and its ffmpeg codec, but what exactly is a mystery to me. Any help is very welcome.

Thanks a lot in advance.

P.S. My script is very large, so I left it out, because I am sure noone wants to trawl through 1000s of lines of code.

---

