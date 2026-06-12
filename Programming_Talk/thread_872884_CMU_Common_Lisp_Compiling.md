---
title: "CMU Common Lisp Compiling"
date: 2008-07-28
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-07-28
When compiling CMU Common Lisp, can you compile to executable machine code or is it byte code that Lisps then executes?

Can you provide a link to an example of either or both?

---

### Post by Kadrus on 2008-07-28
To compile:
```
compile-file ("/pathtofile.lisp")
```
Then load the file:
```
load ("/pathoffile.lisp")
```
[CMUCL Documentation]("http://www.cons.org/cmucl/doc/index.html")

---

### Post by Mr.Macdonald on 2008-07-28
That didn't answer my question.

Is compilation like Java's or C's?

---

### Post by Kadrus on 2008-07-28
Common Lisp implementations do not have a compiler, it's not the same as a C++,Java,etc. compilers where it spits out raw machine language which will link into a native binary.. You still have to invoke the main Lisp binary and tell it to load and execute the FASL.

---

### Post by Alasdair on 2008-07-28
Both SBCL and CMUCL will compile to native machine code. I think SBCL compiles everything including things you type in the REPL, while CMUCL has both a compiler and an interpreter (don't quote me on that though :)). Lisp is different from other languages in that you need the entire lisp system available at run-time. You can either achieve this by loading compiled fasl files into your lisp system, or you can use a function like sbcl's save-lisp-and-die to create a binary executable like you would in any other compiled language.

---

### Post by CptPicard on 2008-07-28
... the only nasty problem being that save-lisp-and-die saves everything so you get a huge binary :( There is no tree-shaker unfortunately there...

---

### Post by Alasdair on 2008-07-28
Clisp produces much smaller binaries than SBCL or CMUCL, although they are still pretty huge when compared with other languages. However using GZip I was able to compress a 15.8MB clisp program all the way down to just 2.42MB.

---

### Post by Nemooo on 2008-07-28
I thought CLISP only produced byte code. Am I misunderstanding something or is it just old information?

---

