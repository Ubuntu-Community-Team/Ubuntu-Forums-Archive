---
title: "Archive Manager and tarballs"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by sirius56 on 2008-07-20
Suppose you download a program which is a .tar.bz2 file.  After downloading, Archive Manager opens to help you with unzipping and unpackaging. What is not clear to me is the proper destination for a downloaded program file?   Most applications (or a symbolic link to them) seem to end up in  /usr/bin. Does it matter where you download a program as long as a symbolic link to the program is entered in /usr/bin?


I have a similar question for codecs.   Suppose I want to download dirac-codec to listen to the BBC.  What is the proper destination for codecs?

---

### Post by Pro-reason on 2008-07-20
You are almost certainly asking the wrong question.

If you don't know where codecs go, then you are probably not someone who should be downloading source-code tarballs and suchlike, but instead be searching for packages in Synaptic.  95% of the time, the software you want is there.

If you want to use the command line:
```

sudo apt-get install **dirac**

```

---

### Post by t0p on 2008-07-20
> **sirius56 said:**
> Suppose you download a program which is a .tar.bz2 file.  After downloading, Archive Manager opens to help you with unzipping and unpackaging. What is not clear to me is the proper destination for a downloaded program file?   Most applications (or a symbolic link to them) seem to end up in  /usr/bin. Does it matter where you download a program as long as a symbolic link to the program is entered in /usr/bin?


When you download an app in a tar archive, you generally don't need to worry about where the program's going to end up - you're not going to put it there yourself.  You extract to your Desktop or wherever you decide, go into the resulting folder and do your **./configure make make install** thing, and the finished program will end up in its final home automagically.  Generally speaking.  Just check the **INSTALL** and **README** files in the folder you extract, that'll tell you what you need to know.

---

### Post by sirius56 on 2008-07-21
> **Pro-reason said:**
> You are almost certainly asking the wrong question.

If you don't know where codecs go, then you are probably not someone who should be downloading source-code tarballs and suchlike, but instead be searching for packages in Synaptic.  95% of the time, the software you want is there.

If you want to use the command line:
```

sudo apt-get install **dirac**

```



My tarball interest was in the 5% not satisfied by Synaptic.  tOp gave me the answer I needed.

---

### Post by sirius56 on 2008-07-21
After asking the question, I found an excellent reference on installing packages:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

