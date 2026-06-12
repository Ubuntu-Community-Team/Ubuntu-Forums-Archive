---
title: "Banshee, Clementine not working"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by Izver on 2011-11-03
I installed Lubuntu, works great - only problem is that "out of the box" only music application that works is Audacious. Both Clementine and Banshee will display selected mp3 or flac files "greyed out", and will just skip them, as if they are deleted.

Any help?

---

### Post by wolfen69 on 2011-11-03
You need the proper codecs first.
```
sudo apt-get install lubuntu-restricted-extras
```

---

### Post by Izver on 2011-11-03
Thanks for the tip - did what you said, codecs installed OK, but the behavior remains the same. Removed Clementine, installed it again - no luck. Audacious still works without problems. Any other suggestion?


> **wolfen69 said:**
> You need the proper codecs first.
```
sudo apt-get install lubuntu-restricted-extras
```

---

### Post by Izver on 2011-11-04
This did the trick:

```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```

> **Izver said:**
> Thanks for the tip - did what you said, codecs installed OK, but the behavior remains the same. Removed Clementine, installed it again - no luck. Audacious still works without problems. Any other suggestion?

---

