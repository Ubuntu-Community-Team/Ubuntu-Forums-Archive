---
title: "Create .deb from a simple .py program?"
date: 2006-07-03
forum: Programming Talk
---

### Post by chanders on 2006-07-03
Hello

I want to make a Debian Package of my program in python.. This program uses the pyGTK+ library. Is there an easy way to do this? I cant seem to find a howto that is geared towards Python :neutral: 

Thanks in advance

---

### Post by dabear on 2006-07-03
Didn't you read Senori's reply?
[http://www.ubuntuforums.org/showpost.php?p=1210923&postcount=48](http://www.ubuntuforums.org/showpost.php?p=1210923&postcount=48)
Also, take a look at the developers guide by pressing F1 (when not in a browser like flock or firefox)

---

### Post by xtacocorex on 2006-07-04
Another idea you could use is to create a makefile that installs the files where you want them and then install checkinstall.

To build the .deb, at the terminal (in the program source folder) type
```
sudo checkinstall
```

This will build a .deb.

I know it's not make the correct way, but it works.

---

