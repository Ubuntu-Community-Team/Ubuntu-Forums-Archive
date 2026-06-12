---
title: "coding on windows but compile and run on linux"
date: 2016-03-02
forum: Programming Talk
---

### Post by afrugh on 2016-03-02
hi
i'm using notepad++ for writing the source code basic things actually
so i configured samba or let's say added some sharing lines in smb.conf like explained in server guide
but how to save directly without moving the files from one directory (c:\..) to shared directory (:\\linux\share) ?

thank u

---

### Post by spjackson on 2016-03-03
Have I got this right? You want to save a file created in Notepad++ directly to a network share? If that's what you are asking then:
1. Google for "Map a network drive" and follow the instructions.
2. In Notepad++ do File->SaveAs N:\path\if\required\mysource.some-extension

---

### Post by afrugh on 2016-03-03
@spjackson 
Thanks. I found another easier solution. I first create the empty files in linux, and then open them from windows with Notepad++.
It is working..

---

### Post by Andy_Richardson on 2016-03-12
Just from reading your title, if you're looking to compile and run programs in a linux-like environment then you might want to use minigw or cygwin

---

