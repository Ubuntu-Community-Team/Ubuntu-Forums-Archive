---
title: "Lisp???"
date: 2008-11-26
forum: Programming Talk
---

### Post by Enalia on 2008-11-26
Okay, let me start off by saying that programming-wise I'm no n00b. Linux wise I'm probably just a step above 'n00b'.  I decided, mostly on a whim, that I should really like to see what all this LISP business is about.

There are tons of posts everywhere and they all seem to say... nothing.

If anyone's done this what I'm asking is for a tutorial from start to finish on how you got LISP working, and then maybe a tutorial from start to finish to make a simple LISP program.

Really, at this point, just a tutorial to get LISP installed and then a tutorial on how to 'compile' or 'run' or whatever it is with LISP... get run through the code and do whatever it is LISP does.

Why this will benefit the community:
While most of us (as I'm sure a lot of you are thinking) are completely capable of trudging through all the vague and confusing documentation out there.  There seems to be a lot of trial and error involved and some people really like to keep their systems clean.

If I sound rather demanding and unwilling to find things out myself, I'm sorry, but really nothing should be this frustrating to figure out.

---

### Post by jimi_hendrix on 2008-11-26
pick your dialect:

Common Lisp:
   more features and more popular

Scheme:
  minimalist lisp with some things that CL does not have

---

### Post by Enalia on 2008-11-26
I would go with common lisp.  More popular means more tutorials and/or documentation. And once I get the basics of lisp I can move on to Scheme if I like.

---

### Post by jimi_hendrix on 2008-11-26
online book

[http://gigamonkeys.com/book/](http://gigamonkeys.com/book/)

---

### Post by Cracauer on 2008-11-26
I don't recommend anything else than Common Lisp except for when you want to work through a book that uses Scheme, such as SICP. My Common Lisp of choice is SBCL.

For compilations etc. you should try forget SLIME running. If not that then a shell buffer in emacs might kinda do, but you lose much of what Lisp is about.

---

### Post by CptPicard on 2008-11-27
> **Enalia said:**
> I would go with common lisp.  More popular means more tutorials and/or documentation. And once I get the basics of lisp I can move on to Scheme if I like.

You've got it somewhat backwards... CL is more complex for "practical reasons" -- you're more likely to "move on" *from* Scheme if you like, as that is the quicker way to get "in to" Lisp... :)

I am somewhat partial to Scheme for "academic reasons" although I use SBCL to actually code stuff... sometimes paring things down to essentials is a good thing.

---

### Post by nvteighen on 2008-11-27
> **CptPicard said:**
> You've got it somewhat backwards... CL is more complex for "practical reasons" -- you're more likely to "move on" *from* Scheme if you like, as that is the quicker way to get "in to" Lisp... :)

I am somewhat partial to Scheme for "academic reasons" although I use SBCL to actually code stuff... sometimes paring things down to essentials is a good thing.
And I still ask myself why my FreeTruco project (see sig) is written in Scheme... :p

Scheme is a great tool to learn Lisp and also some programming concepts, with the help of the MIT Press SICP book/lectures (which is the best Scheme "tutorial" out there... actually meant to be an introduction to programming).

SICP book (online)
[http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-1.html#titlepage](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-1.html#titlepage)

SICP videos (really worth)
[http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/)

Then you could look at other Lisps... Common Lisp, Clojure, Emacs Lisp, whatever.

---

### Post by Cracauer on 2008-11-27
This is what I recommend to go through, with Common Lisp:

Paradigms of Artificial Intelligence Programming: Case Studies in Common Lisp 
by Peter Norvig 
[http://www.amazon.com/Paradigms-Artificial-Intelligence-Programming-Studies/dp/1558601910/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1227813867&sr=8-2](http://www.amazon.com/Paradigms-Artificial-Intelligence-Programming-Studies/dp/1558601910/ref=pd_bbs_sr_2?ie=UTF8&s=books&qid=1227813867&sr=8-2)

[img]http://ecx.images-amazon.com/images/I/41Y2FDAAE4L._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU01_.jpg[/img]


Also, there's a on-web free book "On Lisp" by Paul Graham, which goes through Common Lisp macros, although I prefer Norvig.

---

### Post by Shin_Gouki2501 on 2008-11-27
i hope this helps you:
[http://ubuntuforums.org/showthread.php?t=951509](http://ubuntuforums.org/showthread.php?t=951509)

---

### Post by Shin_Gouki2501 on 2008-12-04
Hey have you tried this?
[http://github.com/aemoncannon/las3r/wikis](http://github.com/aemoncannon/las3r/wikis)

---

