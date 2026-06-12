---
title: "select and move all files from a directory and its subdirectories"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by crowhill on 2008-08-28
hi there


i'm facing the following situation:

given a directory with some files and subdirectories in it, which in turn might contain not only files but also further subdirectories (and so on and on ...).

here's what i want to do:

i'd like to select all files and only the files from the directory and all its subdirectories. next, i'd like to move them to some other directory.

here's my obvious question:

how can i achieve the above selection and motion most efficiently?

hope to hear back from you,
thanks a lot in advance,
cheers,

crowhill.

---

### Post by unutbu on 2008-08-28
```
cd SOURCE_DIR
find . -type f -print0 | xargs -I{} -0 cp {} TARGET_DIR
```

This will find all the files in SOURCE_DIR (including subdirectories) and copy them to TARGET_DIR, without recreating the subdirectories.

---

### Post by ilrudie on 2008-08-28
```
find . -type f -exec cp {} TARGET_DIR \;
```I think that should work as well and its a little more compact.  Also you execute it from the directory you want to do this in... thats what the dot after find means.  Alternatively you can put any full or relative path in therein place of the dot.

---

### Post by crowhill on 2008-08-28
great! thanks a lot for the prompt reply. it works perfect :) i doubt you can do this as easily with win-stuff ... ? ...

cheers,
crowhill.

---

### Post by LAKOSWOLF on 2009-11-10
I just thought I would mention that this post saved me HOURS worth of work, Thank you!:popcorn:

---

