---
title: "debugger"
date: 2007-11-17
forum: Packaging and Compiling Programs
---

### Post by jakubdaniel on 2007-11-17
Hi guys it's pretty possible that it should be in other forum but i didnt know where to post it.

so, i downloaded [http://ald.sourceforge.net/](http://ald.sourceforge.net/) and i tried to install it

[B]./configure
make install[/B]
.
.
.
Making install in source
make[1]: Entering directory `/tmp/ald-0.1.7/source'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../libDebug/include -I../libDASM/include -I../libOFF/include -I../libString/include    -g -O2 -DNDEBUG -MT readln.o -MD -MP -MF ".deps/readln.Tpo" -c -o readln.o readln.c; \
        then mv -f ".deps/readln.Tpo" ".deps/readln.Po"; else rm -f ".deps/readln.Tpo"; exit 1; fi
[COLOR="Blue"]readln.c:25:31: error: readline/readline.h: No such file or directory
readln.c:30:30: error: readline/history.h: No such file or directory[/COLOR]
make[1]: *** [readln.o] Error 1
make[1]: Leaving directory `/tmp/ald-0.1.7/source'
make: *** [install-recursive] Error 1

^ this is what i get ^

and i dont know what i should search for, what to install, like i can see that there is something missing :) but i dont know if its supposed to be part of the install or is it a dependency?

---

### Post by bapoumba on 2007-11-17
Moved to "Packaging and Compiling Programs".

---

### Post by wolfbone on 2007-11-17
Is this not in the package repositories? If it isn't, it looks like you need the development package for readline and you may find you need others. If you are just looking for a debugger, why not use gdb anyway? It's actively developed, full-featured and has GUI interfaces such as ddd and emacs's new one.

---

### Post by jakubdaniel on 2007-11-17
well thx for recommendations but lets stick with the question whats wrong with it, shall we?

i heard that ald is better then gdb

"Is this not in the package repo.." well i dont know what package name i should be searching for

---

### Post by jakubdaniel on 2007-11-17
please any suggestions

---

### Post by NathanB on 2007-11-17
It appears that you need to issue this command:
```

$ sudo apt-get install build-essential

```

Please excuse the rudeness of the previous posters -- they have their "noses in the air" with the haughty assumption that you should have read the "sticky" threads on these forums which explain these steps.

---

### Post by jakubdaniel on 2007-11-17
thx for replies and suggestions
well i am sorry if i missed something but i aint expert, actually i am pretty new to linux

I am still having some difficulties
the same error appears

---

### Post by NathanB on 2007-11-17
Oops!  Sorry.  Some of us already have the support library installed due to other apps depending on it.  I believe you want to launch Synaptic and do a search for "readline"... just to cover all bases, make sure you have "libreadline5", "libreadline5-dev", and "readline-common" marked for installation.

---

### Post by jakubdaniel on 2007-11-17
there the main issue comes i think ... synaptical search for readline gives me nothing

oh sry, it was frozen ... now there are some results


so i got it installed THX A LOT, (i am sometimes slow :))

---

### Post by wolfbone on 2007-11-17
> **NathanB said:**
> Please excuse the rudeness of the previous posters -- they have their "noses in the air" with the haughty assumption that you should have read the "sticky" threads on these forums which explain these steps.


Would you please explain, NathanB, exactly what is rude about my previous post.

---

### Post by NathanB on 2007-11-18
> **wolfbone said:**
> Would you please explain, NathanB, exactly what is rude about my previous post.

Some people prefer to compile from source.  Sometimes, one has no other choice but to compile from source.  The OP's query was a "How to compile?" type of question.  It was moved into this "Packaging and Compiling Programs" subforum which is _supposedly_ intended as a resource for providing "How to compile?" type of answers.  I admit that "rude" and "haughty" are probably too strong of words, so let us just say that when the _answer_ that the OP receives is "Is this not in the package repositories?", it is indeed a bit odd and un-helpful.  If we do not address "How to compile?" issues directly, then this subforum loses its focus.

---

