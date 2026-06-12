---
title: "How to quickly find files by name in CLI"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by dmitrijledkov on 2008-06-03
On mac there was this great command locate. You just type in "locate *.el" and it would extremely fast spit out every file (with full path) which ends with .el

Is there something similar on Ubuntu? How to install it? How to configure it to work?

---

### Post by SunnyRabbiera on 2008-06-03
actually that command does exist in linux, as OSX and linux share many commands with eachother thanks to both being unix based/ unix like.

---

### Post by akiratheoni on 2008-06-03
> **dmitrijledkov said:**
> On mac there was this great command locate. You just type in "locate *.el" and it would extremely fast spit out every file (with full path) which ends with .el

Is there something similar on Ubuntu? How to install it? How to configure it to work?

I just did a "locate *.el" and it spit out all of the files with the full path with the extension *.el. So yeah, it's the same command :)

---

### Post by dmitrijledkov on 2008-06-03
Yeah cool =D

I think it matters which directory your in. Cause when I was deep in my home nothing appeared. But when I went to "cd /" I got LOADS =D

---

### Post by akiratheoni on 2008-06-03
Really? I got the same results no matter what directory I am in.

---

### Post by dmitrijledkov on 2008-06-03
> **akiratheoni said:**
> Really? I got the same results no matter what directory I am in.

strange. for me it looks only for what's in current dir or child dirs, but not parent.

---

### Post by The Cog on 2008-06-03
Don't forget that * gets expanded by the shell to a list of all files in the current directory. Not what you want at all. Use the command **echo *** to see what I mean. 
Use single quotes to prevent the shell expansion and allow the * to pass through to the locate command:
```
locate '*.el'
```

Also remember that the locate database is only updated periodically so won't contain the names of very recent files. **sudo updatedb** will re-scan (I think).

---

### Post by hyper_ch on 2008-06-03
and if it's a new file you try to locate, you might need to manually update the slocate db first
```

sudo updatedb

```

or use "find" instead

---

