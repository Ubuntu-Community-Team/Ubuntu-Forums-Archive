---
title: "Save to a shared folder on another box?"
date: 2008-12-11
forum: Programming Talk
---

### Post by EvilMarshmallow on 2008-12-11
I've got a script that generates a file.  It's on box1.  I want to save a copy of the file to a wide-open shared folder on box2.  I have checked and permissions will allow me to do this... I just need to know how to construct the bash statement that will save it on another box.  I'm sure it's pretty simple, I've just never done it before and google wasn't really sure what I was talking about.

---

### Post by mssever on 2008-12-11
That question can't be answered without knowing what kind of share it is and how it's shared. If the directory is mounted like a regular filesystem (it would show up in the mount command's output), then there's nothing special--just write to the proper path. If it's mounted through some other method (such as Nautilus), then you'll have to use a separate program that knows how to handle those kinds of shares.

---

