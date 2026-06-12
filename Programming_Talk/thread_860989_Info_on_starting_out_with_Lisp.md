---
title: "Info on starting out with Lisp"
date: 2008-07-16
forum: Programming Talk
---

### Post by ceclauson on 2008-07-16
Hello.  I'm interested in starting out with Lisp, but most of the information on the internet about Lisp is of the abstract, theoretical kind.  I'm currently stuck on the mundane details, like these:
1) Is Lisp compiled or interpreted or both? Where can I get a compiler/interpreter?
2) What can I do with Lisp?  Is it extensible and/or embeddable, or have some other mode with which it can interface with native code?

Thanks in advance,
Cooper

---

### Post by CptPicard on 2008-07-16
> **ceclauson said:**
> Hello.  I'm interested in starting out with Lisp, but most of the information on the internet about Lisp is of the abstract, theoretical kind.

First of all, a lot depends on the specific Lisp. Some things are in common, and let's assume you mostly mean Common Lisp here...

> 
1) Is Lisp compiled or interpreted or both? Where can I get a compiler/interpreter?

Kind of both. There is typically incremental compilation of functions you define into either bytecode or machine code. SBCL in particular is native-compiling, but Lisps also have a runtime "shell" (the REPL) which is crucial for the dynamic programming style which is pretty great and half of the fun of coding in Lisp. You really need to try it, it's hard to understand from an explanation :)


> 
2) What can I do with Lisp?

"Anything". GUI libs on Linux seem to be lacking though.

> 
  Is it extensible

Lisp is all about being extensible. Lisp gods essentially code by defining mini-languages using macros, which are small code-transformation programs.

> 
 and/or embeddable

A lot of lisps are extension languages, because writing an interpreter is so simple... Emacs in particular is so very extensible because it's coded on top of an Emacs-Lisp interpreter.

However, doing something like embedding larger Lisp environments like SBCL somewhere would probably be very hard because the Lisp programming model is so very different from anything else.

> or have some other mode with which it can interface with native code?

Yeah, you can call native code, but again depends on your implementation.

---

### Post by ankursethi on 2008-07-16
As such, the Common Lisp standard only defines the language itself. The standard does not say whether Lisp should be compiled or interpreted and hence the language implementors can choose between compiling to native code, byte code or interpreting the code.

I generally use clisp. clisp is an interpreter, but can optionally compile to FASL bytecode. FASL files are fast loading files. Compiling to FASL will have no impact on your program's performance, but there will be a reduction in the time it takes to load your source file. FASL files are very much like Python's pyc files.

BTW, head over to [http://gigamonkeys.com/book](http://gigamonkeys.com/book) to get a taste of Lisp. If you want a faster paced tutorial, purchase a copy of Paul Graham's *ANSI Common Lisp*.

---

### Post by skeeterbug on 2008-07-16
Check out [http://www.lisp.org/alu/res-lisp-tools](http://www.lisp.org/alu/res-lisp-tools) as well.

---

### Post by ceclauson on 2008-07-16
Okay, I guess this will probably get me started.

Thanks all.

---

### Post by CptPicard on 2008-07-16
For a good environment try out SBCL and the cusp Eclipse plugin (google it).

If you want something off beaten path, my favourite pet lisp at the moment is definitely Clojure...

---

