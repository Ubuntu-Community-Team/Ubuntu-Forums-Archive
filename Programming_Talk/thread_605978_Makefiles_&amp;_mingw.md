---
title: "Makefiles &amp; mingw"
date: 2007-11-07
forum: Programming Talk
---

### Post by Vadi on 2007-11-07
Hello,

I'm developing an app (learning as I go along) in C. The app itself has several compontents, and I use a single Makefile for compiling them all. Originally, the makefile wasn't written by me, and I couldn't find any docs on it (I have just a Makefile, not a Makefile.am or Makefile.in), however that wasn't a problem as I figured out the basics of manipulating it.

The program is compiled on both Linux and Windows, on Windows, it uses the mingw compiler. However, the Makefile for the windows one is completely different from the Linux one - but again, I learned from the previous things in it, and added lines to it as needed.

But recently, I needed to re-work the makefile to define some flags. I had a friend who helped me get it working, but the problem is, he doesn't know how to edit the windows one. Neither do I still, so I'm quite stuck - the windows version is very important still.

So I was hoping if someone could help me translate the linux makefile into the windows one? Or, point me to good documentation on the windows makefiles for mingw? 

Thank you very much if you're able to help me on either of the terms. I've attached the makefiles if anyone could help - the first two are the original ones, and the third one is the modified linux one. I appended .txt on them so they'll be a valid attachment.

---

### Post by Vadi on 2007-11-08
Could anyone help?

---

### Post by Vadi on 2007-11-08
Nevermind, the issue has been solved.

---

