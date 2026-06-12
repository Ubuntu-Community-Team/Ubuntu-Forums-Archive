---
title: "I installed unpacked Candido Engine...now what?"
date: 2006-07-21
forum: Packaging and Compiling Programs
---

### Post by UberIcarus on 2006-07-21
No, seriously, now what? It tells me to go to the directory with the source code, which I assumed is usr/lib/gtk-2.0/2.4.0/engines

and then run ./configure

Ubuntu is not recognizing that as anything. I'm assuming a different command used for compiling in ubuntu? (Newbie, never compiled a thing in my life)

---

### Post by SDREnate on 2006-07-22
Well, if you used the Ubuntu package to install the Engine, then I'm pretty sure it's already installed for you and you don't have to compile anything. If you downloaded the source code and extracted it, then you would compile it like this.
```
cd /path/to/extracted/folder
```
```
./configure --prefix=/usr --enable-animation
```
Then:
```
make
```
Finally:
```
make install
```

edit- That's just how to install the engine. After that I don't know what you have to do to run it.

---

