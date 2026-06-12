---
title: "[Python] Trying to load a dll"
date: 2008-12-29
forum: Programming Talk
---

### Post by dodle on 2008-12-29
I'm trying bass.dll

```
from ctypes import *

mp3Play = windll.LoadLibrary("bass.dll")

musicFile = "Kitty.mp3"
mp3Play.BASS_MusicLoad(musicFile)
```

Error:
> ValueError: Procedure probably called with not enough arguments (16 bytes missing)

---

### Post by catchmeifyoutry on 2008-12-29
Hmm, isn't that Windows specific? This is an ubuntu linux forum, are you using ubuntu? Probably wont find much help for windows specific programming problems here as most people here cannot reproduce your problems. Also, if you somehow are trying to get ctypes.windll working on ubuntu it will not work (unless you're running python in Wine ...etc... nevermind).

---

### Post by neonive on 2011-04-11
[http://blog.dt.in.th/2010/12/using-bass-in-python/]("http://blog.dt.in.th/2010/12/using-bass-in-python/")

Here is an example of loading BASS in Python on Linux.

Maybe you can get some hints from it.

[: neonive

---

### Post by cariboo on 2011-04-11
Thread closed, as it's 3 years old. I doubt if the op is still looking for an answer to the question.

---

