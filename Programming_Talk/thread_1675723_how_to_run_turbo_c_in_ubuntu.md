---
title: "how to run turbo c in ubuntu???"
date: 2011-01-26
forum: Programming Talk
---

### Post by Praveen30 on 2011-01-26
hi guys,

i am running some programmes on gcc compiler and i have to check same  programmes on turbo c compiler.But i do not have this c turbo compiler.i  have done some searching and found that it is not possible to install  turbo c directly ,for this i have to use dosbox.ok now the main question  is that for this i must have c++ setup which i do not have...so plz  suggest me some links so that i can download this setup..(plz suggest  sites which do not require any registration)

---

### Post by bcz on 2011-01-26
Try System/Administration/Synaptic...

Do a search for g++  and install it

g++ will do your C++ compiles from a terminal widow

Enjoy

---

### Post by worksofcraft on 2011-01-26
> **Praveen30 said:**
> hi guys,

i am running some programmes on gcc compiler and i have to check same  programmes on turbo c compiler.But i do not have this c turbo compiler.i  have done some searching and found that it is not possible to install  turbo c directly ,for this i have to use dosbox.ok now the main question  is that for this i must have c++ setup which i do not have...so plz  suggest me some links so that i can download this setup..(plz suggest  sites which do not require any registration)

Turbo C is a developer tool that runs under Windows and a quick Google reveals that it is now available for free from sites like [http://www.bestfreewaredownload.com/freeware/t-free-turbo-c--freeware-flggsdpz.html](http://www.bestfreewaredownload.com/freeware/t-free-turbo-c--freeware-flggsdpz.html).

It may be possible to run it on Ubuntu if you install the [Windows Emultor a.k.a. "wine"]("http://www.winehq.org/") Another way to use it would be to create a [virtual machine]("http://www.virtualbox.org/") on your desktop that runs Windows. Virtual Box is also free, but Windows isn't.

---

### Post by wojox on 2011-01-26
> **Praveen30 said:**
> ok now the main question  is that for this i must have c++ setup which i do not have...so plz  suggest me some links so that i can download this setup..(plz suggest  sites which do not require any registration)

All you need is:

```
sudo apt-get install build-essential
```

---

### Post by Praveen30 on 2011-01-26
> **worksofcraft said:**
> Turbo C is a developer tool that runs under Windows and a quick Google reveals that it is now available for free from sites like [http://www.bestfreewaredownload.com/freeware/t-free-turbo-c--freeware-flggsdpz.html](http://www.bestfreewaredownload.com/freeware/t-free-turbo-c--freeware-flggsdpz.html).

It may be possible to run it on Ubuntu if you install the [Windows Emultor a.k.a. "wine"]("http://www.winehq.org/") Another way to use it would be to create a [virtual machine]("http://www.virtualbox.org/") on your desktop that runs Windows. Virtual Box is also free, but Windows isn't.

thanks, there is also an another way.you must have a look on this-->

[http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html](http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html)

---

### Post by alaukikyo on 2011-01-26
> **worksofcraft said:**
>  [Windows Emultor a.k.a. "wine"]("http://www.winehq.org/") 

the full form of WINE is Wine Is Not an Emulator.

---

### Post by worksofcraft on 2011-01-26
> **Praveen30 said:**
> thanks, there is also an another way.you must have a look on this-->

[http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html](http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html)

lol - actually I did try to get qualified once upon a time and they wanted us to use Turbo Pascal in a DOS environment... I kind of lost interest in the course at that point :shock:

> **alaukikyo said:**
> the full form of WINE is Wine Is Not an Emulator.

ok... it's not something I ever use... it does emulate Microsoft Windows on a Posix platform though doesn't it?

---

### Post by Praveen30 on 2011-01-26
> **worksofcraft said:**
> lol - actually I did try to get qualified once upon a time and they wanted us to use Turbo Pascal in a DOS environment... I kind of lost interest in the course at that point :Shock:



ok... it's not something I ever use... it does emulate Microsoft Windows on a Posix platform though doesn't it?

i know, believe me it is not very interesting.but finally i am able to run turbo c under dosbox..thanks worksocraft...the main thing which i was unable to get, was the setup which i  got from your link....i think me and c2tarun(we are friends) have become a fan of you....

---

### Post by alaukikyo on 2011-01-26
> **worksofcraft said:**
> ok... it's not something I ever use... it does emulate Microsoft Windows on a Posix platform though doesn't it?

no it doesn't(which is quite clear by its real full form0.
it is a compatibility layer which allows windows programs to run on posix without windows.

---

### Post by alaukikyo on 2011-01-26
> **worksofcraft said:**
> ok... it's not something I ever use... it does emulate Microsoft Windows on a Posix platform though doesn't it?

no it doesn't(which is quite clear by its real full form).
it is a compatibility layer which allows windows programs to run on posix without windows.

---

### Post by Praveen30 on 2011-01-29
for step by step installation visit here---
[http://tricksfind.blogspot.com/2011/01/how-to-run-turbo-c-in-ubuntu.html](http://tricksfind.blogspot.com/2011/01/how-to-run-turbo-c-in-ubuntu.html)

---

