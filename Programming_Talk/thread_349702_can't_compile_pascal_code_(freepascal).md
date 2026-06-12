---
title: "can't compile pascal code (freepascal)"
date: 2007-01-30
forum: Programming Talk
---

### Post by xpan on 2007-01-30
Hi, 

I installed freepascal using synaptics. 

However whenever I try to compile a simple "hello world" application I get this message:

Fatal: Can't find unit System

any ideas?

---

### Post by Stemp on 2007-01-30
What about gpc : The GNU Pascal compiler ?

---

### Post by angustia on 2007-01-30
did you installed those?
fp-compiler  <- here is the compiler fpc
fp-units-base <- here base units, with system
fp-units-rtl     <- more base units

---

### Post by xpan on 2007-01-31
yes, I have installed those packages.

Concerning the gpc, I tried it and it works, but when I try to use crt ("uses crt;") I get:

hw.pas:1: warning: missing program header
hw.pas:1: error: module/unit interface `crt' could not be imported

why is this so complicated?

---

### Post by kacike on 2007-03-15
I have the same problems here (with both fpc and gpc). Let me know if you find an answer.

---

### Post by xpan on 2007-03-15
I finally used "dosbox" and turbo pascal for dos. 

It is easy and works nice. Try it, and let me know if you have any problems! :)

---

### Post by kacike on 2007-03-15
It worked great! Thanks!

---

