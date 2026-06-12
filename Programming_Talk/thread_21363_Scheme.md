---
title: "Scheme"
date: 2005-03-21
forum: Programming Talk
---

### Post by trivialpackets on 2005-03-21
Anyone ever used scheme?  I'm learning C++ and was told that in the future, they will be teaching scheme for new programmers.  Wondering if anyone has tried it, I'm thinking about giving it a spin in my free time and if there's a compiler for it in Ubuntu.  I'd look, but I'm no where near Ubunut now.  Thanks all.

---

### Post by dcraven on 2005-03-21
The package called mzscheme is the interpreter you want for Scheme. DrScheme is a somewhat popular dev tool as well. Vim also handles it just fine as I'm sure Emacs does as well.

I learned Scheme and Prolog in an 'alternative' languages course. One functional and one logical. It was a great experience just to see how non-procedural languages work. I suggest it or Lisp for all programmers just for kicks. It's useful, Lisp is especially useful if you are an Emacs user.

Cheers,
~djc

---

### Post by toojays on 2005-03-22
Scheme is very cool, and lots of fun to learn. I highly recommend the [SICP book](http://www-mitpress.mit.edu/sicp/), it has lots of problem solving techniques which you don't tend to see in C++ books.

The GNU scheme interpreter is in Ubuntu main as guile-1.6. Whatever scheme interpreter you use, you can integrate it into Emacs quite nicely by adding something like ```
(setq-default scheme-program-name "guile")
``` to your .emacs.

---

