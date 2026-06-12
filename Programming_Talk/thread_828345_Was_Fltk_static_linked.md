---
title: "Was Fltk static linked?"
date: 2008-06-13
forum: Programming Talk
---

### Post by techmarks on 2008-06-13
I did a little test app in using Fltk it compiled to a
size of 220,208 seems large for such a little app.

Then I did more or less the same thing in GTK and the
size was 15,858 bytes (actually was a bit more complicated 
than the Fltk one)

So I'm guessing when I use the following command;

$ fltk-config --compile hello.cc

That the Fltk library was statically linked,

Does anyone know if that is so?

---

### Post by Nuverde on 2008-06-13
I believe that if you type "file <filename>" it will tell you if the file is dynamically or staticly linked.  I am on a Windows box at work though, so I can't double check.

---

### Post by bruce89 on 2008-06-13
Usually pkg-config is a better way of doing things, but I notice FLTK doesn't have a pkgconfig file.

Have a look at the options fltk-config provides.

---

### Post by techmarks on 2008-06-13
from Nuverde
> I believe that if you type "file <filename>" it will tell you if the file is dynamically or staticly linked. I am on a Windows box at work though, so I can't double check.


Thanks, I tried that and this is what I got;

$ file hello
hello: ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), for FreeBSD 7.0 (700055), dynamically linked (uses shared libs), FreeBSD-style, not stripped
$ 

So that means it was dynamic linked, now the question is why was it so large?

---

### Post by bruce89 on 2008-06-13
> **techmarks said:**
> So that means it was dynamic linked, now the question is why was it so large?

Maybe FLTK is not such a good name for it then.

Have a look at the assembly source to see if it's huge (gcc -S blah).

---

### Post by techmarks on 2008-06-13
> Maybe FLTK is not such a good name for it then.

Have a look at the assembly source to see if it's huge (gcc -S blah).

Now there's an understatement.

How disappointing indeed.  I thought Fltk was supposed to be small, and
could be static linked.

With that size for such a tiny app dynmaic linked, I'd hate to see the 
size of a static link!!

---

### Post by Nuverde on 2008-06-13
I really dont think it should be that large.  It has been years since I used fltk, but that was for a Linux PDA.  (Anyone remember the Agenda VR3?) One of the reasons they picked FLTK was because of its small size.

---

### Post by techmarks on 2008-06-13
> I really dont think it should be that large.


It does seem odd, I've no idea where I've gone wrong.


I used a few globals, but I also used some globals on the GTK version.

The difference of 204.350 bytes, huge discrepancy.

If it's gonna be like this, I might I well continue with GTK.

The thing I didn't like of GTK and the messy OpenGL integration.

---

### Post by bruce89 on 2008-06-13
Does stripping the binary (with *strip*) do anything major?

---

### Post by techmarks on 2008-06-13
> Does stripping the binary (with strip) do anything major?



I tried the strip.

now it's like this

the fltk;

from 220,208 kb to 177,324

the gtk

from 15,838 to 11,904

fltk is still so huge, something went wrong but I don't know
what.

maybe the g++ settings are wrong, but I'm not very good about those.

---

### Post by techmarks on 2008-06-13
I also wonder now if both GTK and Fltk versions are compiled
static, maybe the Fltk will be smaller then?

I'll try this later, I've still not figured it out.

---

### Post by WW on 2008-06-13
> **techmarks said:**
> I did a little test app in using Fltk it compiled to a
size of 220,208 seems large for such a little app.

Then I did more or less the same thing in GTK and the
size was 15,858 bytes (actually was a bit more complicated 
than the Fltk one)

So I'm guessing when I use the following command;

$ fltk-config --compile hello.cc

That the Fltk library was statically linked,

Does anyone know if that is so?

I couldn't find the answer in the FLTK programming manual (maybe I didn't look hard enough), so instead I peeked into the source for fltk-config.  It's just a shell script, so it isn't too hard to figure out.  The answer to your question is *yes*, the --compile option uses static linking of the fltk library.  To use a shared library (if you have one), something like this should work:
```

$ g++ -c hello.cc `fltk-config --cxxflags`
$ g++ hello.o `fltk-config --ldflags` -o hello

```
(But this wouldn't help on my current installation.  I installed FLTK 1.1.9 from source on a Mac, and the only fltk files in /usr/local/lib are .a files.)

---

### Post by techmarks on 2008-06-14
WW> The answer to your question is yes, the --compile option uses static linking of the fltk library


Thanks for checking that.
I suspect you are right...but

If I do 'file' command on executable this is 
what returns;  (hello is name of exe file)


$ file hello
hello: ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), for FreeBSD 7.0 (700055), dynamically linked (uses shared libs), FreeBSD-style, not stripped
$ 

maybe I'm wrong then?  but this seems to say that it was
dynamically linked?

---

### Post by Zugzwang on 2008-06-14
> **techmarks said:**
> maybe I'm wrong then?  but this seems to say that it was dynamically linked?

It could be linked dynamically against another library (glibc, for example) while being statically linked to FLTK at the same time.

---

### Post by geirha on 2008-06-14
the ldd command should print all the libraries that are dynamically linked. If it's not listed there, it's probably statically linked.
```
ldd hello
```

---

### Post by WW on 2008-06-14
> **techmarks said:**
> WW


Thanks for checking that.
I suspect you are right...but

If I do 'file' command on executable this is 
what returns;  (hello is name of exe file)


$ file hello
hello: ELF 32-bit LSB executable, Intel 80386, version 1 (FreeBSD), for FreeBSD 7.0 (700055), dynamically linked (uses shared libs), FreeBSD-style, not stripped
$ 

maybe I'm wrong then?  but this seems to say that it was
dynamically linked?
Some libraries can be statically linked while others are shared.  One way to statically link a single library is to explicitly give the .a file when linking (instead of using the -l option).  This is apparently what fltk-config does:
```

$ fltk-config --ldflags
[color=blue]-L/usr/local/lib -lfltk[/color] -lpthread -framework Carbon -framework ApplicationServices
$ fltk-config --ldstaticflags
[color=blue]/usr/local/lib/libfltk.a[/color] -lpthread -framework Carbon -framework ApplicationServices
$

```
The differences are shown in blue.  (Remember that I'm on a mac at the moment, with fltk installed from source into /usr/local; you won't see exactly the same output in Linux.)  With --ldstaticflags, fltk-config simply gives the .a file; this binary file will be incorporated into the executable (i.e. the library is static linked).  Other libraries can still be dynamically linked.

---

