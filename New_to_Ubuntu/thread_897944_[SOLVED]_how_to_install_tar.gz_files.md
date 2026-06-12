---
title: "[SOLVED] how to install tar.gz files"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by enri2 on 2008-08-22
how? I extracted the files and has a bunch of other tar files and a setup with like a script icon

---

### Post by bubba_169 on 2008-08-22
Is it a source file or a binary program? Try opening a terminal, using the cd command to get to the directory you extracted your files to, then running sudo ./setup

If its a source archive then you will need to build it and sorry but I dont have much experience there...

---

### Post by Elfy on 2008-08-22
This should answer your questions, but before you start opena terminal and do these to get ahead

```
sudo apt-get build-essential checkinstall
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Remeber that linux is case sensitive and if it says cd Desktop do that :)

---

### Post by Cheesehead on 2008-08-22
Back to basics: What are you installing?
An app?
A plugin?
A theme?
A font?
A script?

Did it come with instructions or README? If so, what does it say?

---

### Post by enri2 on 2008-08-22
bubba's method worked , thanks

---

