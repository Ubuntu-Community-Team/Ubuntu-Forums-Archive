---
title: "Cross-compiling from 32bits to 64bits."
date: 2010-11-05
forum: Programming Talk
---

### Post by gugahoa on 2010-11-05
I looking for how to cross-compile from 32bits to 64bits with g++, and i fail. ):

i was searching it for some hour and i found this forum, and i guess the user's here can help me, i don't know nothing about cross-compiling if someone teach me a little thing it will be good. '-'

Sorry bad english, i'm 14 years old and don't study english so much, only for school. hoho

---

### Post by Arndt on 2010-11-06
> **gugahoa said:**
> I looking for how to cross-compile from 32bits to 64bits with g++, and i fail. ):

i was searching it for some hour and i found this forum, and i guess the user's here can help me, i don't know nothing about cross-compiling if someone teach me a little thing it will be good. '-'

Sorry bad english, i'm 14 years old and don't study english so much, only for school. hoho

When I asked a similar question (in a another forum), I was pointed to [http://www.virtualbox.org/](http://www.virtualbox.org/). But I solved my problem in another way, so I haven't actually used VirtualBox.

Don't worry about your English, I understood you fine.

---

### Post by gugahoa on 2010-11-06
My internet is 'humble', only 256kbytes(32kb/s on download), and i need this fast, can u tell me another way? :S


ooh, i forgot:

Thank you for answer me. *-*

---

### Post by Arndt on 2010-11-06
> **gugahoa said:**
> My internet is 'humble', only 256kbytes(32kb/s on download), and i need this fast, can u tell me another way? :S


ooh, i forgot:

Thank you for answer me. *-*

The way I solved my problem was simple but uninteresting: I went and built the program on the target system, after first installing the packages my program needs.

Why do you need 64-bit, actually? Programs built for 32-bit will run on 64-bit without changes.

---

### Post by gugahoa on 2010-11-06
Cuz i have one game server, who has 8gb of ram, and use Ubuntu 32bits with PAE, and tha game is 'freezing', isn't to freeze, i guess it is conflict between PAE and the server because it needs more than 4GB of RAM, if isn't that i'll need to install Ubuntu 64bits and run a new server executable.

/\ cuz that i need to compile to 64bits. '-'

PS: If i compile on dedicated server, the executable will be 32bits


If u want, i have more one trouble:

The server take 21% of memory and don't have nothing running on machine, only the server, but when i do 'free -m' show me i'm using 7gb of memory, what is that? :/

---

### Post by linux-hack on 2010-11-06
Normally a program compiled on a 32bit system works on a 64 also, but not the other way.

---

### Post by gugahoa on 2010-11-06
> **linux-hack said:**
> Normally a program compiled on a 32bit system works on a 64 also, but not the other way.


i know that, but a 32bits program running on 64bits os isn't the same of the same program 64bits running on 64bits os.

---

### Post by wmcbrine on 2010-11-06
**-m64**

But you need the appropriate libraries and headers installed.

```
$ gcc -m64 test.c
In file included from /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from test.c:1:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
```

Personally I've only done it the other way (-m32, for building 32-bit executables on 64-bit systems).

---

### Post by gugahoa on 2010-11-06
> **wmcbrine said:**
> **-m64**

But you need the appropriate libraries and headers installed.

```
$ gcc -m64 test.c
In file included from /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from test.c:1:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory
```Personally I've only done it the other way (-m32, for building 32-bit executables on 64-bit systems).

I have already tried this.

~~

SOLVED: I sais to my friend to compile for me. '-'

---

