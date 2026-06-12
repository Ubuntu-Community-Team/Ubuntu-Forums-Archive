---
title: "really stupid question..."
date: 2008-02-10
forum: Programming Talk
---

### Post by MikeSz on 2008-02-10
sorry if this has been asked a thousand times before but ive had a look round the forum and there is simply far too much info on this subject but nothing really really basic - which is what I need.

I used to be into programming when I was back at college (over 10 years ago) and we learned C and Pascal.  I have a magazine that starts easy Python projects to get people into programming and thought I would get back into it and start from scratch.

The thing is, where do I start??  Nothing tells me which program I use to start entering and compiling code.  When I did C and Pascal, we had a dedicated editor and compiler provided by Borland.  So can anyone tell me where I start and any tips for things to watch out for when starting out?

---

### Post by popch on 2008-02-10
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

---

### Post by aks44 on 2008-02-10
Doesn't the "Linux Programming Reference" [sticky thread]("http://ubuntuforums.org/showthread.php?t=606009") answer your questions?

---

### Post by MikeSz on 2008-02-10
Many thanks for the replies - I will have a read through!  

Had a look through the sticky and will be going back to it but it seemed to assume you knew a bit about what you were doing so it kind of lost me.

---

### Post by CptPicard on 2008-02-10
Essentially, you just edit your source with any editor of your preference and then do whatever you need to do to compile/run what you wrote. How to run Python code, for example, is very well documented in pretty much all tutorials you're likely to come across...

---

### Post by aks44 on 2008-02-10
Since you mentioned Python... [this beginner's guide]("http://ubuntuforums.org/showthread.php?t=333867#5") is only two clicks away from the sticky... ;)

---

### Post by H264 on 2008-02-10
It depends on what programming language you want to use/learn. One of the things you will be using all the time is the command line (unless you are doing it on windows). at this point its only a matter of time before the python people start *spamming* (j/k - posting), so I will let them describe how to do what in it.

For C, C++, Objective-C, Pascal, Cobol, Fortran, and many others, there is the compiler gcc.. 

```
sudo apt-get build-essential
```
will get you gcc and most everything else related.

then you need to make your C program and save it to the desktop in something like Gedit.
```

#include <stdio.h>
int main(){
    printf("hello world");
    return 0;
}

```
back in the terminal do:
```
cd Desktop
cc myprogram.c
./a.out
```

Have fun :)

EDIT
ah, the python people already beat me to the punch...

---

### Post by pmasiar on 2008-02-10
and check wiki in my sig!

---

