---
title: "Space In Filename In VIM"
date: 2013-06-03
forum: Programming Talk
---

### Post by huangyingw on 2013-06-03
Hello,
    Bellowing is the content of my file```
huangyingw@laptop:~/myproject/git/test_fw$ cat couldyoufindme.fww.findresult 
"./dir space/name space.cc"

```
   When I use vim to open the file couldyoufindme.fww.findresult, when my cursor is on space, I hit "gf", wanting to navigate to the file: ./dir space/name space.cc. But fail, for there is space in the name of that file.
   How could I change the string "./dir space/name space.cc", so it could over come the space issue?

---

### Post by shawnhcorey on 2013-06-05
Try:
```
"./dir space/name\\ space.cc"
```

---

### Post by trent.josephsen on 2013-06-05
Use your primary resources first

```
:help gf
```

---

### Post by huangyingw on 2013-06-09
thanks. this one does not works.

---

### Post by huangyingw on 2013-06-09
> **shawnhcorey said:**
> Try:
```
"./dir space/name\\ space.cc"
```
thanks, this one does not work.

---

