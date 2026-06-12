---
title: "Vim script - passing full path of file"
date: 2007-11-09
forum: Programming Talk
---

### Post by pylon42 on 2007-11-09
(Very new to vim, scripting and everything else)

I have a script that requires a full path be passed to it:

scriptName /home/blah/blah/blah

I'm doing so in Vim like this currently:

! scriptName %

I thought % was the full path, but apparently it's just the relative path. Is there a symbol or something similar for the full path?

---

### Post by weresheep on 2007-11-09
Hello,

I don't know of anyway in VIM to get the full path of the current file. However, perhaps its possible to modify your script to work with a relative path.

If you could post a little more info about your script maybe we can spot an alternative way of accomplishing what you need.

-weresheep

---

### Post by geirha on 2007-11-09
!scriptname `pwd`/% should give an absolute path that works, though it might not be the shortest one. Whether vim has a special symbol for it or not, I have no idea. Vim has too many features :)

---

### Post by stylishpants on 2007-11-09
```

! scriptname %:p

```

---

