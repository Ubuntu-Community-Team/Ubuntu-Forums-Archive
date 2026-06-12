---
title: "QT,pigz,GUI"
date: 2011-07-22
forum: Programming Talk
---

### Post by snip3r8 on 2011-07-22
I'm working on a GUI for the pigz file compressor,I've attached a screen-shot,all i want is some feedback on its design

---

### Post by Jacks0n on 2011-07-25
You might want to make the number of threads hidden, and set it with ```
QThread::idealThreadCount()
``` so it's even easier for the user, but it'll utilize all available cores.

---

### Post by snip3r8 on 2011-07-25
Latest ScreenShot

---

### Post by snip3r8 on 2011-07-26
> **Jacks0n said:**
> You might want to make the number of threads hidden, and set it with ```
QThread::idealThreadCount()
``` so it's even easier for the user, but it'll utilize all available cores.

I feel that the user likes some power so i might just add "auto" as an option

---

### Post by snip3r8 on 2011-07-26
Here is an updated screenshot with the automatic thread selection,thanks for the input by the way.

---

### Post by snip3r8 on 2011-07-26
[http://sourceforge.net/projects/qpigz/](http://sourceforge.net/projects/qpigz/)

---

### Post by snip3r8 on 2011-08-03
now out of beta - version 1.0.1 - Does anyone Know how to make a .deb package?

---

### Post by cgroza on 2011-08-03
> **snip3r8 said:**
> now out of beta - version 1.0.1 - Does anyone Know how to make a .deb package?

You could contact a Debian developer to package it for you. You will need more than a deb package to get it in the repos if that is what you want to do.

---

### Post by akoskm on 2011-08-03
> **snip3r8 said:**
> now out of beta - version 1.0.1 - Does anyone Know how to make a .deb package?

Since you are double posting maybe you don't discovered yet that I already answered in your second thread.

---

