---
title: "[SOLVED] Pure Lisp"
date: 2008-12-29
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-12-29
I have been learning Common Lisp and to learn I started watching these videos.
[HERE]("http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/")

I began to like scheme (the language in the videos) because it seemed more "Pure". There isn't any defvar or defun, it just define and variables can be executed as functions without funcall. 

Is Scheme more like the original definition of Lisp or are all implementations different from the original? 

Is their an original definition of Lisp out their and if so how does its usability and moderniality compare to Common and Scheme Lisps?


Also if anyone can point me to challenges for Lisp, or should I use Project Euler?

---

### Post by CptPicard on 2008-12-29
I really am not sure what old lisps have looked like, but Scheme has specifically been built with minimalism in mind, because it was meant to be a teaching tool from the outset. IMO they succeed quite well, and I like Scheme for the same reasons as you do -- it's very elegant and doesn't have anything in the way that doesn't need to be there. It's about as compact as it can get, while still being as powerful (meaning language design perspectives here...)

Another interesting lisp you may like is Clojure. It seeks to be more "pure" in the pure-functional sense.

---

### Post by Cracauer on 2008-12-29
> **Mr.Macdonald said:**
> I have been learning Common Lisp and to learn I started watching these videos.
[HERE]("http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/")

I began to like scheme (the language in the videos) because it seemed more "Pure". There isn't any defvar or defun, it just define and variables can be executed as functions without funcall. 

Is Scheme more like the original definition of Lisp or are all implementations different from the original? 

Is their an original definition of Lisp out their and if so how does its usability and moderniality compare to Common and Scheme Lisps?


Also if anyone can point me to challenges for Lisp, or should I use Project Euler?

McCarty's original Lisp book is still in print, I have it floating around somewhere.

It wasn't as minimalistic as Scheme, but of course not as bloated as Common Lisp (nothing is...). You have variables and some extra syntax.

I don't think that either are particularly usable without hacking them up with more OS integration support. Which I think is only worth doing for Common Lisp.

If you want challenges, work through this books:
[http://www.amazon.com/Paradigms-Artificial-Intelligence-Programming-Studies/dp/1558601910/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1230604791&sr=8-2](http://www.amazon.com/Paradigms-Artificial-Intelligence-Programming-Studies/dp/1558601910/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1230604791&sr=8-2)

---

### Post by Mr.Macdonald on 2008-12-29
I tried to install scheme but had problems

mit-scheme didn't work, it blew up.
mzscheme also blew up
quile just sucked, I couldn't use arrow keys!!!! withour getting their values printed to screen.

What Scheme do you use and where do I get it, I want to make scripts and have history (like in shells, up key to see past entries). Basically just a really nice interactive (non-gui) interface and shell scriptability.

Thank You

---

### Post by Cracauer on 2008-12-29
"Blew up" is hardly an actionable piece of diagnosis :)

I don't use Scheme.

For Common Lisp I use SBCL and CMUCL.

---

### Post by Mr.Macdonald on 2008-12-29
mit-scheme give this after installing from apt-get

scheme: error while loading shared libraries: libmhash.so.2: cannot open shared object file: No such file or directory


mzscheme gave a big mess of errors that I don't have right now

---

### Post by Mr.Macdonald on 2008-12-29
I found scm and am pretty happy now, but other schemes are welcome

---

### Post by Sorivenul on 2008-12-29
> **Mr.Macdonald said:**
> I found scm and am pretty happy now, but other schemes are welcome
Ikarus is relatively new on the Scheme market and I've been playing with it a bit lately.

Gauche is a relatively common implementation also, at least to my knowledge.

For a more complete [list of Scheme implementations]("http://community.schemewiki.org/?scheme-faq-standards#implementations") and other great resources look to [schemers.org]("http://schemers.org/").

---

### Post by nvteighen on 2008-12-30
mit-scheme (MIT/GNU Scheme) is an historically broken package in Ubuntu. In Hardy it won't work if you don't change some kernel variables at /etc/sysctl.conf (see the stickies). In Intrepid there is also a dependency issue (the corresponding bug report: [https://bugs.launchpad.net/ubuntu/+source/mit-scheme/+bug/288000](https://bugs.launchpad.net/ubuntu/+source/mit-scheme/+bug/288000)).

If you want an MIT "official" implementation, there's also MIT Scheme48 (scheme48 in the repos). As long as your implementation complies to the R5RS standard, you're ok (and avoid using implementation-specific extensions if you plan to share your code). Well, it's true that MIT/GNU Scheme's advantage is that it has Emacs-integration...

Scheme is the best language **of which I know** that allows you to understand the problem of abstraction and data modelling. You can do a lot of experimentation with it. Yes, it is not suitable as a "practical" language, but it's nice.

btw, the SICP videos and the SICP book are the best Scheme tutorials out there.

---

