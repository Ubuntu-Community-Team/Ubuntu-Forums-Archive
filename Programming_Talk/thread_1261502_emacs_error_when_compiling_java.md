---
title: "emacs error when compiling java"
date: 2009-09-08
forum: Programming Talk
---

### Post by TheStickyNoteKing on 2009-09-08
I'm trying to make a very simple program in Java, all it does is print two lines. I'm doing this to see if I can use emacs as my IDE... However when I do C-c C-v C-c, I get this error:

Cannot find JDK's tools jar file (or equivalent).Type M-x describe-function [RET] jde-get-jdk-dir for more info.

I'm using emacs22, with no x support. I've saved the file, compiled it with javac, and run it with java, it works like a charm, however emacs should be able to do it all by itself...

Anyone know what is going on? That error message doesn't help at all...

Edit: I can also run the program from emacs with C-c, C-v, C-r, so compiling is the only thing I can't do...

---

### Post by unutbu on 2009-09-08
I do not know java, so I am not speaking from experience.
Have you looked at this thread? Perhaps posts #3,4,8?

[http://ubuntuforums.org/showthread.php?t=316786](http://ubuntuforums.org/showthread.php?t=316786)

---

### Post by TheStickyNoteKing on 2009-09-08
I've tried the stuff in that thread, and am still stubbornly banging my head against the wall doing so. Still getting the same error no matter what I put in the registry...

Edit: Success! I had just pointed it one level deeper than it liked... All I needed was in that other thread after all... Silly me.

---

