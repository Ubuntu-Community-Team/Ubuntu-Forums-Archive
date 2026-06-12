---
title: "Help with python"
date: 2011-07-06
forum: Programming Talk
---

### Post by roodypoo on 2011-07-06
I'm trying to teach myself programming and I was wondering if someone would be kind enough to write  me some psuedocode and list the modules I need for my program.

What I want to do is rename a folder full of files. The folder is full of pictures from my digital camera. I want to rename them 1,2,3,4... ; most of them have the same file extension (.jpg) but some of them are .(png). 

Thanks!

---

### Post by TwoEars on 2011-07-06
Modules:
regex/glob
os/shutil

Algorithm: 

```


x = 1
FOR file IN directory:
    IF file.extension IS 'jpg':
        RENAME file AS x + '.jpg'
    ELSE:
        RENAME file AS x + '.png'
    x = x +1

```

This is a really easy program to make, you will probably only need either os or shutil, but a big of glob/regex practice is always good.

---

### Post by pafoo on 2011-07-06
Nicely done

---

