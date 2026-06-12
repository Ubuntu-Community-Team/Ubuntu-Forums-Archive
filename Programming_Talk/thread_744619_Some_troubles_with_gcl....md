---
title: "Some troubles with gcl..."
date: 2008-04-03
forum: Programming Talk
---

### Post by eleifsp on 2008-04-03
Today I installed GCL (GNU Common Lisp) from Synaptic package manager.  I was using it without trouble until I tried to compile an external file, where I got this error:

> Compiling testing.lisp.
End of Pass 1.  
End of Pass 2.  
testing.c:174:18: error: math.h: No such file or directory
testing.c:269:20: error: setjmp.h: No such file or directory
testing.c:270:19: error: stdio.h: No such file or directory
testing.c:857: error: expected specifier-qualifier-list before ‘FILE’
testing.c:1621: error: expected specifier-qualifier-list before ‘jmp_buf’
testing.c:1982: error: expected declaration specifiers or ‘...’ before ‘size_t’
testing.c:2158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
testing.c:3195:20: error: stdlib.h: No such file or directory
testing.c:3453: error: expected declaration specifiers or ‘...’ before ‘size_t’
testing.c:3453: error: expected declaration specifiers or ‘...’ before ‘size_t’
testing.c:3671: error: expected ‘)’ before ‘*’ token
testing.c:3811:20: error: unistd.h: No such file or directory
testing.c:3853: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
testing.c:3854: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
testing.c:3855: error: expected ‘)’ before ‘*’ token
testing.c:4013: error: expected ‘)’ before ‘*’ token
testing.c:4100: error: expected ‘)’ before ‘*’ token

Correctable error: (SYSTEM "gcc -c -Wall -DVOL=volatile -fsigned-char -pipe  -I/usr/lib/gcl-2.6.8/unixport/../h  -O3 -fomit-frame-pointer -c \"testing.c\" -o \"testing.o\" -w") returned a non-zero value 0.
Signalled by UNLESS.
If continued: Continues anyway.
Broken at CERROR.  Type :H for Help.


If anyone has experience with GCL, some help would be appreciated.  Although, this looks like an error with GCC not being able to import headers...

---

### Post by LaRoza on 2008-04-03
Try:

```

sudo aptitude install build-essential

```

Also, you will find that SBCL and CLisp are more used. GCL has some standards compliance issues I hear. (I use CLisp, but I think SBCL is more popular)

---

### Post by eleifsp on 2008-04-03
That fixed it!  Thanks.  I might look into those other two, but GCL was the only one I found in Synaptic, and I usually try to stick to Synaptic packages (mainly because I've screwed up Ubuntu two or three times).

---

### Post by lnostdal on 2008-04-03
the remedy vs. "screwing up" when working with software outside a distros package manager is of course not to install "outside" software _globally_

install it _locally_ in your home folder instead .. if something "screws up" you simply delete the directory with the software in in your home folder and try again

about packages .. both clisp and sbcl are in the ubuntu repositories

though, i recommend not bothering with them .. install _all_ lisp software (compilers, libraries and apps.) "manually" in your home folder instead .. (edit: this seems like bad/wrong advice coming from a linux background, but it's not -- lisp has its own way of dealing with things and they do not fit well with the linux (a C based OS and world) way of doing things)

quick writeup about sbcl: [http://common-lisp.net/~lnostdal/writings/sbcl.html](http://common-lisp.net/~lnostdal/writings/sbcl.html)

..and yeah, don't bother with gcl .. it's practically dead

---

