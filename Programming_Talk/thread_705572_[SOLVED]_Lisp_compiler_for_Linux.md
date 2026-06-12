---
title: "[SOLVED] Lisp compiler for Linux?"
date: 2008-02-23
forum: Programming Talk
---

### Post by WitchCraft on 2008-02-23
Hi!

Hi, I'm trying to start to learn Lisp.

Can anyone tell me a good Lisp COMPILER (not interpreter or bytecode compiler) ?

I found LispBox, which doesn't compile on my system.
Then I found GLC, the GNU lisp compiler, but I cannot find any documentation on how to actually use it, eg. info on how to compile a simple Lisp "Hello World" sourcecode file...

and i found CMUCL, but there I have the same problem with the documentation...

---

### Post by Fbot1 on 2008-02-23
[http://en.wikibooks.org/wiki/Programming:Common_Lisp/First_steps/Installation#Free_implementations](http://en.wikibooks.org/wiki/Programming:Common_Lisp/First_steps/Installation#Free_implementations)

---

### Post by Jessehk on 2008-02-23
AFAIK, SBCL is the current favorite.

---

### Post by lnostdal on 2008-02-24
you want SBCL

here is a writeup of how i install it:[http://common-lisp.net/~lnostdal/writings/sbcl.html](http://common-lisp.net/~lnostdal/writings/sbcl.html)

note that you can also install SBCL via aptitude/apt-get if you wish

---

### Post by LaRoza on 2008-02-24
> **lnostdal said:**
> you want SBCL

note that you can also install SBCL via aptitude/apt-get if you wish

What about CLisp? Anything particularly wrong with that?

---

### Post by lnostdal on 2008-02-24
> **LaRoza said:**
> What about CLisp? Anything particularly wrong with that?

he wanted a native compiler (CLISP is lisp --> bytecode)

---

### Post by LaRoza on 2008-02-24
> **lnostdal said:**
> he wanted a native compiler (CLISP is lisp --> bytecode)

Ah, I see.

(Still new)

---

