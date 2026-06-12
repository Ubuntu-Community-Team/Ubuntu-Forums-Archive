---
title: "ocaml problems"
date: 2006-10-23
forum: Programming Talk
---

### Post by jworr on 2006-10-23
I installed ocaml on by Ubuntu system but it seems one of the standard library modules is missing. The missing module is "Str" - it handles regular expressions.  I despriately need regular expressions in ocaml for an upcomming project, has anyone else ran into this problem?

---

### Post by coder_ on 2006-10-24
Maybe *sudo aptitude install ocaml-libs?*

Or check in /usr/lib/ocaml/<VERSION>/ to see if the library is there... 

I seemed to get the str module **edit: with version 3.09.1 installed from aptitude.**


I haven't done much in ocaml yet [at all], but I'd really like to try to get into functional programming, but it is kind of different compared to "regular" paradigms...  I can't wait for college...  I would really like to learn about this subject, got any good links?

---

### Post by coder_ on 2006-10-25
*Bump*

After reading more on O'Caml and getting more into it, to open a module up in the Interpreter, you need to do *#load "str.cma";;*, but that is only for the interpreter, otherwise you'd open it like "open Str;;" (If you don't want to have to do Str.foo) and link to it in ocamlc or ocamlopt (depending on if you want bytecode or native code, respectively).

I think this is what you are asking/what your problem is.

---

### Post by jworr on 2006-10-28
sudo aptitude install ocaml-libs

This did it for me thanks. Its strange because most of the other modules worked without this, but thanks again

Note I needed to use the:
#load "str.cma" ;;

---

### Post by jworr on 2006-10-29
You might want to look at:

[http://www.ocaml-tutorial.org/](http://www.ocaml-tutorial.org/)
[http://caml.inria.fr/pub/docs/manual-ocaml/index.html](http://caml.inria.fr/pub/docs/manual-ocaml/index.html)
[http://caml.inria.fr/pub/docs/oreilly-book/html/index.html](http://caml.inria.fr/pub/docs/oreilly-book/html/index.html)
[http://caml.inria.fr/pub/docs/manual-ocaml/libref/index.html](http://caml.inria.fr/pub/docs/manual-ocaml/libref/index.html)
[http://pauillac.inria.fr/~remy/cours/appsem/index.html](http://pauillac.inria.fr/~remy/cours/appsem/index.html)
[http://minimalprogramming.org/html/section.ocaml.quick-tour.html](http://minimalprogramming.org/html/section.ocaml.quick-tour.html)

These sites are mostly practical information about ocaml but it has a little theory too.  Functional programming langauages are very cool but a little harder to get into at first.  The basic idea of functional programming languages is to avoid site affects when writing functions.

---

### Post by coder_ on 2006-10-29
Yeah, designing and writing functions without side effects is tough for me, obviously, being used to C and such.  Thanks for the links. :)

---

### Post by Hezekiah on 2006-11-07
One of the nicest things about OCaml is that you can still program in a non-functional manner if you choose.  I'm still relatively new to the language, but I've already had a chance to use it for a relatively major project related to some thesis research I'm doing and I'm very impressed.  Another nice bonus is how easily it can be used with C - the interface is (IMHO) very simple and easy to use, at least for basic tasks.

Also, the fact that you can use it interactively, as an interpreter (!#/usr/bin/ocaml), as a bytecode compiled language and as a machine code compiled language is wonderful for rapid development and testing.

---

