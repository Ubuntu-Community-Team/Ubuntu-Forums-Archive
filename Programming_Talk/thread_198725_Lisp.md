---
title: "Lisp"
date: 2006-06-17
forum: Programming Talk
---

### Post by bieber on 2006-06-17
I've looked into Lisp a little bit, and it seems to be a very interesting language, one that I'd definitely like to learn, if only for the sake of knowing it.  However, I'm unsure as to whether it is a feasible development platform for sizable applications.  Is there a way to compile Lisp programs to native code?  Also, is there a way to interface GTK+ with them?

---

### Post by mostwanted on 2006-06-18
Lisp is very fragmented and I looked at it briefly a while ago, but didn't find anything I dared to dive into; Gtk+ Clisp libs aren't in the Ubuntu repos, so I though it was too indie to start programming Lisp.

---

### Post by bieber on 2006-06-18
Well, I've started learning using clisp to interpret code.  It's definitely a language I like, although I don't think I'll ever try GUI programming in it, since, as you mentioned, the libs aren't in the repositories.  I've figured out how to get GCL to compile to byte code, but does anyone know of a way to get it to compile to native code?  Or else a seperate utility that will fully compile the .fas files?

---

### Post by rickardg on 2006-06-19
I've always found [CLiki]("http://cliki.net") a very useful resource. The pages on [GTK-bindings]("http://www.cliki.net/GTK%20binding") and [Graphics toolkits]("http://www.cliki.net/Graphics%20Toolkit") are probably  good starting points.

---

### Post by moriarty on 2006-07-22
I'm trying my hand at lisp now. It's definitely a language worth learning. I'm not very far yet, but about GUI programming, there's a library called cells-gtk that seems very interesting.
I ran the demo and looking at the source for it, it does seem to make GUI programming pretty easy. I never tried implementing anything in it yet, so I don't know how well it works in practice.
Also if anyone knows what the best way is to get SLIME working in Ubuntu, please drop me a line. CMUCL is good enough for me at the moment.

---

### Post by Daverz on 2006-07-22
For gtk Lisp bindings, clg seems like the most complete.  I got the clg demos working with sbcl, which I downloaded from the sbcl site because the ubuntu version is so old.

As for the language itself, I've only poked at it a bit, working through some of *Practical Common Lisp*.  It's definitely a very powerful and expressive language, but there does seem to be a lack of critical manpower in the community for things like libraries and packaging.  I think I'll probably take a detour via PLT Scheme, particularly as that is used in some very interesting CS texts like SICP.

---

### Post by chris hyperstring on 2006-11-17
i'm finding lisp alot easier to learn than html and all the windows programming, mostly cos i can get on well with algebra as thats basicaly what it is!

im trying to find a way of checking the memory usage on sbcl, and its proving a dog :( aparently there is a line of code that does it but im not sure what it is, can anybody help please?

---

### Post by Steve Pullman on 2006-11-17
Scheme is, I think, quite close to Lisp.
The Gauche implementation has GTK and OpenGL extensions.
It's great for learning to program.

---

### Post by krzysz00 on 2009-04-26
sbcl compiles to native code

---

### Post by Sinkingships7 on 2009-04-26
> **krzysz00 said:**
> sbcl compiles to native code

If only you were here two and a half years ago. :P

---

### Post by spontaneity on 2009-04-26
Clojure will do the trick.  [http://www.clojure.org/](http://www.clojure.org/)

---

### Post by CptPicard on 2009-04-26
> **chris hyperstring said:**
> i'm finding lisp alot easier to learn than html and all the windows programming, mostly cos i can get on well with **algebra as thats basicaly what it is**!

Ding ding ding, we have a winner! I'm glad someone gets this from the get-go. This is a very important observation that holds for functional programming in general, not just Lisp, which is more of a multiparadigm language. What you essentially do is write stuff in terms of data transformations by functions, and compose and break up functions quite freely. Due to the homoiconicity of the language, you also get a front-end macro compiler that allows for complete Turing-complete freedom to abstract the syntax, within and by the language itself. All this while keeping the core of the language minimal yet powerful enough to support all the fundamental core concepts -- there are *very few* special constructs. It has everything, but nothing more.

This way, you really get a kind of "algebra" for your problem domain. It's very mathematical in its feel, yet very practical.

And as was pointed out above, SBCL compiles to native code (there is a somewhat odd fascination with native-compilation among some people... *most* software requires runtime support or libraries). There is of course a "runtime environment/library", and in Lisp, the REPL running in this "lisp image" is actually just unbelievably interactive and handy. You can literally build stuff while it exists right there in memory, and run parts of it...

---

