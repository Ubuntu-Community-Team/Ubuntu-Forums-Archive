---
title: "cant get semantic to work"
date: 2009-10-17
forum: Programming Talk
---

### Post by samush on 2009-10-17
Hi, 
I' installed semantic with synaptic yesterday and I haven't  managed to get it to work.
Loading the library in emacs works fine but when I try to start the code completion with M-x semantic-complete-analyze-inline then I get:
```
semantic-analyze-current-context: Wrong type argument: syntax-table-p, nil
```How do I get semantic to work?

---

### Post by jpkotta on 2009-10-18
I do not use Cedet.  It looks very interesting, but I haven't had the motivation to dive in.

It seems like older versions of Cedet don't build properly with the Emacs in Ubuntu (note: build mostly means bytecompile, but it probably involves other things too).  I use emacs-snapshot from the emacs-lisp PPA, and also keep emacs22 around.  I got cedet-1.0pre4 from Sourceforge to build with emacs22, but I got the same error as you when trying to run that function.  I checked out Cedet CVS and it built with emacs-snapshot, and I no longer get the error.  I loaded the cedet library and other things as specified on the Cedet website.

FWIW, I use auto-complete with ac-dabbrev for completion.

---

