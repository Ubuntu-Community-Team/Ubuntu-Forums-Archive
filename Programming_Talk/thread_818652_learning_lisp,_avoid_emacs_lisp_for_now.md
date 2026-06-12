---
title: "learning lisp, avoid emacs lisp for now?"
date: 2008-06-04
forum: Programming Talk
---

### Post by dbd on 2008-06-04
Hi,

I'm about to start learning lisp, and was wondering which variant to start with. I already know C++, and want to try out a language which encourages radically different ways of thinking about things, and lisp looks like it might me it.

I'm also currently just starting off learning emacs (I was a vi fan, but wanted to check out the competition), so at first it seemed sensible to learn emacs lisp first, but now I'm not so sure. I was reading the introduction to Practical Common Lisp, and that said:
> Although it's possible more lines of Elisp and Autolisp have been written than of any other dialect of Lisp, neither can be used outside their host application, and both are quite old-fashioned Lisps compared to either Scheme or Common Lisp. If you've used one of these dialects, prepare to hop in the Lisp time machine and jump forward several decades.
If emacs lisp is so backwards and different, then maybe I should go straight for learning Common Lisp (using slime), and then go back to look at emacs lisp afterwards, if I get the urge to mod emacs. Or is the difference less significant than the book claims and therefore just learning emacs lisp first makes sense, seeing as I'll be using emacs?

Thanks

---

### Post by CptPicard on 2008-06-04
I would say EmacsLisp is only for modding Emacs, not a language you should learn on its own right. And when you've got Common Lisp under your belt, EmacsLisp is not that different.

So yes, I'd recommend you start with the SBCL+SLIME+CL combination. It's a nice environment to hack in.

Interestingly, my own Lisping recently has happened with Clojure, a modern JVM-based Lisp. It fixes a lot of stuff I find annoying or missing in CL, and has some fancy concurrency stuff in addition.

---

