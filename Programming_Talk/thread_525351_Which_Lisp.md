---
title: "Which Lisp?"
date: 2007-08-14
forum: Programming Talk
---

### Post by ankursethi on 2007-08-14
I've just grabbed a copy of Practical Common Lisp and now I'd like to dive into Lisp, but the problem is that I don't know exactly what to install.

Do I aptitude install clisp? And then how do I get to use it from an IDE? Also, Emacs works well with Lisp interpreters (being written in it), so how do I use clisp from within Emacs? What about using it with something else? And WTF is Emacs Lisp? I want a sort of general purpose Lisp that I can use to produce binaries which can be mailed to my friends.

And what about Scheme? Is Scheme going to do me any good? Remember, I'm not learning this just for an experience, but as a viable alternative to the monstrosity that is C++. I might decide to learn Haskell or D in the future.

---

### Post by Arwen on 2007-08-14
For Lisp:[http://packages.ubuntu.com/dapper/virtual/lisp-compiler]("http://packages.ubuntu.com/dapper/virtual/lisp-compiler")
Why don't you try java?

---

### Post by ankursethi on 2007-08-14
I'd rather compile to native code than to a VM, otherwise I would have chosen Java/C# a long time back. Also, I'm interested in functional programming, having done bloody-minded-pounding-of-fists-programming using C++ and now-where's-that-manual-programming with Perl. Since I've already looked at Python and (to a small extent) Perl and PHP, CLisp is the next thing I want to try.

Looks like the lisp-compiler metapackage is messed up. It didn't install anything! Anyway, I manually installed all 3 of the listed package.

---

### Post by pmasiar on 2007-08-14
> **ankursethi said:**
>  I want a sort of general purpose Lisp that I can use to produce binaries which can be mailed to my friends.

I'm not learning this just for an experience, but as a viable alternative to the monstrosity that is C++. I might decide to learn Haskell or D in the future.

If you want to learn **mainstream** dynamic language, I recommend Python (see wiki in my sig for links). I believe that Python is used more than Lisp, Scheme, Haskel and D combined :-) according to [TIOBE](http://www.tiobe.com/tpci.htm), which is as misleading and meaningless statistics as any other :-)


Python is multi-paradigm language (old-style procedural, new OOP, even functional programming).

Couple of links for [functional programming in Python](http://www.google.com/search?q=%22functional+programming%22python): 
- [http://www.diveintopython.org/functional_programming/index.html](http://www.diveintopython.org/functional_programming/index.html)
- [http://www.ibm.com/developerworks/library/l-prog.html](http://www.ibm.com/developerworks/library/l-prog.html)
- [http://www.freenetpages.co.uk/hp/alan.gauld/tutfctnl.htm](http://www.freenetpages.co.uk/hp/alan.gauld/tutfctnl.htm)
- [http://www.amk.ca/python/writing/functional](http://www.amk.ca/python/writing/functional)

---

### Post by ankursethi on 2007-08-14
Thanks for the links, but I already know and use Python :-) I forgot to mention it? My bad.

By the way, I have run into some problems with XEmacs and SLIME. It seems to be using CMU Common Lisp. Isn't that the Carnegie Mellon implementation? I want it to use clisp (the ANSI Common Lisp) or SBCL. How do I do that?

Also, I want SLIME loaded at Emacs startup, and slime-mode as default for all .lisp and .cl files. A small SLIME tutorial would be helpful. The "official" tutorial is not much help.

---

### Post by ankursethi on 2007-08-15
Bump!

Help, please!

---

### Post by bread eyes on 2007-08-15
Emacs Lisp is intended to extend emacs. IMHO it kinda sucks a lot. There are two that I can suggest: Common Lisp and Scheme. Common Lisp is implemented better but some still like scheme a lot more. I'd go with Common Lisp. Also, you might like Clean.

---

### Post by Ubuntist on 2007-08-15
> **ankursethi said:**
> 
And what about Scheme? Is Scheme going to do me any good? Remember, I'm not learning this just for an experience, but as a viable alternative to the monstrosity that is C++.

Scheme is the most beautiful, fun and elegant language I've ever played with. But for practical everyday work, I've decided to focus on CL, because:[LIST=1]
[*]CL is fast (usually within a factor of 2 or so of C, according to [the shootout]("http://shootout.alioth.debian.org")); and
[*]The formally-defined Scheme language has no object system. Since Scheme is very powerful, you can roll your on object system if you want to, but that's not where I want to focus my energy.[/LIST]These drawbacks are both overcome to some extent by specific implementations, such as MzScheme, but it's still not that fast and I don't want to be tied to one implementation.

CL has the drawback that it's full of historical baggage. For that reason, I've been keenly looking into some new alternative Lisps such as[LIST]
[*][[COLOR=Blue]Goo[/COLOR]]("http://people.csail.mit.edu/jrb/goo/"), under development at MIT
[*][COLOR=Blue][Otter]("http://groups.google.co.uk/group/comp.lang.lisp/browse_thread/thread/e2764cbec47cbe57/5c597b31df6be557#5c597b31df6be557")[/COLOR], which apparently had its first public showing yesterday in NY, and
[*][COLOR=Blue][Arc]("http://www.paulgraham.com/arc.html")[/COLOR], the new Lisp from guru Paul Graham for which the Lisp community has been waiting for a long time (and still is waiting).[/LIST]My understanding is that the authors of all three of the above are big Scheme fans and are aiming to develop a smaller, modernized Lisp suitable for heavy-duty use.

---

### Post by Ubuntist on 2007-08-15
> **ankursethi said:**
> 
By the way, I have run into some problems with XEmacs and SLIME. It seems to be using CMU Common Lisp. Isn't that the Carnegie Mellon implementation? I want it to use clisp (the ANSI Common Lisp) or SBCL. How do I do that?


I had a similar problem trying to run SBCL under Emacs. My effective though inelegant solution was to create an executable file called
```
/usr/local/bin/lisp
```which contains the two lines
```

#!/bin/bash -f
sbcl

```> 
Also, I want SLIME loaded at Emacs startup, and slime-mode as default for all .lisp and .cl files.
If you figure these out, please let me know. I suspect the key is editing the .emacs file (or maybe .xemacs file in your case?).
 > 
A small SLIME tutorial would be helpful. The "official" tutorial is not much help.
Please let me know about that too.

---

