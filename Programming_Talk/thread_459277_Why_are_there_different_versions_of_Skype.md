---
title: "Why are there different versions of Skype?"
date: 2007-05-30
forum: Programming Talk
---

### Post by Kalixa on 2007-05-30
I was wondering, since Skype is built using the QT toolkit why do the mac, windows and Linux version's differ so much from each other? Is it built on a >QT4 version? Or is Skype such a complicated program that QT's cross platform abilities just aren't enough?

---

### Post by Cappy on 2007-05-30
There is a discussion about this on the skype forums:
[http://forum.skype.com/index.php?showtopic=84988](http://forum.skype.com/index.php?showtopic=84988)

---

### Post by pmasiar on 2007-05-31
this blog post [Python blackhat tools ?](http://www.larsen-b.com/Article/222.html) links to slides (from BlackHat Europe 2006 conference) where they analyzed Skype, and analyzed code obfuscation. Obviously, this obfuscation needs be done differently for every OS.

BTW very interesting read about anti-debugging techniques used (and overcome) by very smart python code. :-)

---

### Post by ankursethi on 2007-06-01
Have you seen the 1.4 alpha of Skype? It looks radically different from it's Windows counterpart (which in my view is a Good Thing). It's just their philosophy that each system must have a separate client which can take advantage of system specific API's and blend well with it rather than having on "cross platform" app.

---

