---
title: "problems with make command and X11"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by GrizlyMedve on 2012-05-24
After nearly 20 years being a MS Windows user I have decided to change to linux because of several usage problems that I came across. My choice was Ubuntu 12.04 LTS and for the past 7 days I had no problem with it, although I was very afraid to "port"!!! But so far I was able to do whatever I wanted to do on it, and the system works flawlessly. (very happy about it!):)
Now that I felt that I had familiarized myself with the "basics" I thought that I will do some research on the 3D in linux as I am a big enthusiast/hobbyist in 3D
I have downloaded 2 books for it! (Linux 3D graphics programming & Advanced Linux 3D graphics programming written by Norman Lin)
I have also downloaded all the necessary apps that it was asking for (Emacs, g++, xxgdb)
On it's first 'tutorial' I should compile a hello.cc ... It keeps giving me error messages!!! until now I was able to solve them as Google is a good friend of mine.
But now it gives me a messages that I can't find anywhere!
after giving the make command in the appropriate folder that's what I see:
```
g++  -O3  -c -o hello.o hello.cc
g++ -L/usr/X11R6/lib -lX11 -lXt -lm hello.o -o hello
hello.o: In function `main':
hello.cc:(.text.startup+0x2a): undefined reference to `XOpenDisplay'
hello.cc:(.text.startup+0x9d): undefined reference to `XCreateWindow'
hello.cc:(.text.startup+0xb3): undefined reference to `XStoreName'
hello.cc:(.text.startup+0xbf): undefined reference to `XMapWindow'
hello.cc:(.text.startup+0xd3): undefined reference to `XSelectInput'
hello.cc:(.text.startup+0xec): undefined reference to `XCheckWindowEvent'
hello.cc:(.text.startup+0x118): undefined reference to `XLookupString'
collect2: ld returned 1 exit status
make: *** [hello] Error 1

```I guess that the problem is with the X11R6 part because I think this ubuntu is using a newer version of X11.  Did I miss a library to install or is it enough to change the command within the makefile? Or none of these and the problem is more complex?:confused:
Please give me a step by step guide to solve this!:lolflag:

---

### Post by roelforg on 2012-05-24
Put hello.o before the libs.

---

### Post by GrizlyMedve on 2012-05-24
:lolflag:
Thank you very much!!! it helped!
The syntax changed recently or the writer made this syntax mistake?

How do I give you a bean or thumb up or something for this help!;)

):P

---

### Post by roelforg on 2012-05-24
> **GrizlyMedve said:**
> :lolflag:
Thank you very much!!! it helped!
The syntax changed recently or the writer made this syntax mistake?

How do I give you a bean or thumb up or something for this help!;)

):P

It's not the syntax, just that the linker is picky about the order.
I always use this syntax for my g++ (the flags are the same for gcc) (it's a little slower but helps a lot with circular dependencies):
```

g++ <includepaths,libpaths> -Wl,--start-group <libs> <object/source files> -Wl,--end-group -o <pathtooutfile>

```

---

