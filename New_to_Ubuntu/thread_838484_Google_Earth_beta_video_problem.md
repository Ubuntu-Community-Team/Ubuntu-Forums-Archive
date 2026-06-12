---
title: "Google Earth beta video problem"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by cartisdm on 2008-06-23
I just installed the newest release of Google-Earth (4.3).  Everything seems to be working great on it but is having a hard time displaying the video.  When it loads up the "world" revolves around but the screen keeps flashing like it's having a seizure.  My whole screen doesn't do it, just the window within Google Earth.  I know it's their beta version but does anyone else have this problem?

Btw I'm running Hardy

---

### Post by cartisdm on 2008-06-30
anyone?

---

### Post by sayakb on 2008-06-30
Before you run Google Earth, open a terminal and type in:
```
metacity --replace &
```

After closing Google earth, do:
```
compiz --replace &
```

---

### Post by cartisdm on 2008-06-30
Thanks bro, worked great!

---

### Post by sayakb on 2008-06-30
Glad I could help. Btw, if you want to try running Google Earth with Compiz without having to switch to Metacity, read this: [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

If you are already happy enough, please mark the thread as solved. :)

---

