---
title: "Compiling 32 bit on 64 bit Ubuntu not working..."
date: 2010-10-24
forum: Programming Talk
---

### Post by Daniel0108 on 2010-10-24
Hi!
I already searched on Google for hours now, about this problem....
Nothing worked for me....
My problem..
I have a c++ program, I want to compile for 32bit pc's... I have 64bit Ubuntu..
64bit compiling worked well, no errors :)
I read that I have to add -m32 to compile for 32 bit...
So far so good...
There was the SDL 32bit library missing... I downloaded it...
Okay...
Now the lstdc++ 32bit is missing... I downloaded, but it always says:
```
g++ -m32 main.cpp -o Bubbles32 -lSDL -lSDL_ttf -lstdc++ -Wall
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

```
How can I fix this?
Please help me,
Yours,
Daniel

---

### Post by Zugzwang on 2010-10-25
Try installing the "g++-multilib" package. It contains non-native library versions for many standard libraries.

---

### Post by Daniel0108 on 2010-10-25
Hi!
I currently upgraded from 10.04 to 10.10 :)
I entered your command..
Now I get:
```
g++ main.cpp -o Bubbles32 -lSDL -lSDL_ttf -m32
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../libSDL.so when searching for -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../libSDL.a when searching for -lSDL
/usr/bin/ld: skipping incompatible //usr/lib/libSDL.so when searching for -lSDL
/usr/bin/ld: skipping incompatible //usr/lib/libSDL.a when searching for -lSDL
/usr/bin/ld: cannot find -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../libSDL_ttf.so when searching for -lSDL_ttf
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../libSDL_ttf.a when searching for -lSDL_ttf
/usr/bin/ld: skipping incompatible //usr/lib/libSDL_ttf.so when searching for -lSDL_ttf
/usr/bin/ld: skipping incompatible //usr/lib/libSDL_ttf.a when searching for -lSDL_ttf
/usr/bin/ld: cannot find -lSDL_ttf
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

```
I need some libs for 32bit :P But don't know where to download them ;)
Yours,
Daniel

---

### Post by Zugzwang on 2010-10-25
> **Daniel0108 said:**
> I entered your command..


Which command?

Note that there is a tool for installing 32-bit libraries on a 64-bit system. I'm not sure if it helps you, but you might want to give it a try:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Eragon0605 on 2010-10-25
You could always download the i386 .deb file from [http://packages.ubuntu.com/](http://packages.ubuntu.com/), manually extract the needed files, and then copy them into your /usr/lib directory.

---

### Post by MadCow108 on 2010-10-25
> **Eragon0605 said:**
> You could always download the i386 .deb file from [http://packages.ubuntu.com/](http://packages.ubuntu.com/), manually extract the needed files, and then copy them into your /usr/lib directory.

better use dpkg -i --force-architecture instead of manual extracting.
Or extract them to some other directory (like /usr/local/lib) and give that path to the compiler

and you still seem to be missing g++-multilib.

---

### Post by Daniel0108 on 2010-10-26
> **MadCow108 said:**
> and you still seem to be missing g++-multilib.
Yeah, that's right, I was missing it on my 10.04.. and installed it ;) Now I formatted my harddisk and installed 10.10 :) And thought I already installed it ;)
I used getlibs and installed the g++-multilib.
Now it's working :D
THANKS :D
Yours,
Daniel

---

### Post by ryry46d9 on 2011-06-28
> **Zugzwang said:**
> Try installing the "g++-multilib" package. It contains non-native library versions for many standard libraries.


Thank You

---

