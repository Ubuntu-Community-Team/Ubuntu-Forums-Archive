---
title: "Command line: Convert a DVD to avi?"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-10
Hello,

I have found an old DVD of a very old movie. I would like to make a backup of it, of small size. about 650-700MB of a divX or Xvid... How to make it. Also if there are by chance subtitles on i, how can I add them? 

With command line ;)

Thanks

---

### Post by papibe on 2011-09-10
This [thread]("http://ubuntuforums.org/showthread.php?t=273635") have lots of useful information. The main post use mencoder and mplayer, but there are more examples with other tools on the rest of the thread (ffmpeg, mkvmerge, MP4Box, etc).

Hope it helps,
Regards.

---

### Post by andrew.46 on 2011-09-10
I documented my own personal method here:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

Mind you it does not use avi container or xvid but could be easily adjusted...

---

### Post by MrWES on 2011-09-10
> **honeybear said:**
> Hello,

I have found an old DVD of a very old movie. I would like to make a backup of it, of small size. about 650-700MB of a divX or Xvid... How to make it. Also if there are by chance subtitles on i, how can I add them? 

With command line ;)

Thanks
```
vobcopy -m
```

```
man vobcopy
```

Bill

---

