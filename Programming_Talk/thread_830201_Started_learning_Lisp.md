---
title: "Started learning Lisp"
date: 2008-06-15
forum: Programming Talk
---

### Post by Timdejager on 2008-06-15
Hi,

I've started to learn Lisp with the Practical Common Lisp book. And it is going alright. 
But I just have a few questions, which implementation of LISP should I use CLISP or SBCL? Is there another IDE or editor for linux which supports Lisp not counting SLIME because i've never worked with Emacs before and feel somewhat more comfortable in a 'normal' text editor. And finally is there a lisp reference somewhere with a list of available functions and a description for each function?

Thanks,

Tim

---

### Post by Acglaphotis on 2008-06-15
SCiTe has lisp support, maybe that'll help you.

---

### Post by Balazs_noob on 2008-06-15
i have just tried lisp but check this
[http://www.sergeykolos.com/cusp/intro/](http://www.sergeykolos.com/cusp/intro/)
it is a lisp plugin for eclipse....

---

### Post by LaRoza on 2008-06-15
> **Timdejager said:**
> Hi,

I've started to learn Lisp with the Practical Common Lisp book. And it is going alright. 
But I just have a few questions, which implementation of LISP should I use CLISP or SBCL? Is there another IDE or editor for linux which supports Lisp not counting SLIME because i've never worked with Emacs before and feel somewhat more comfortable in a 'normal' text editor. And finally is there a lisp reference somewhere with a list of available functions and a description for each function?


CptPicard or lars could help more, but it doesn't matter if you use Clisp or SBCL. CLisp lacks a few things, but they aren't something you'd be using in the beginning anyway.

Check out my wiki for Lisp, you might find some useful information.

Scheme is another Lisp you might want to check out. It is "smaller".

---

### Post by Timdejager on 2008-06-15
> **Balazs_noob said:**
> i have just tried lisp but check this
[http://www.sergeykolos.com/cusp/intro/](http://www.sergeykolos.com/cusp/intro/)
it is a lisp plugin for eclipse....

This is quite nice thanks, it works quite well on my ubuntu box i just had to unzip the sbcl.zip and point eclipse in the right direction and it works like a charm. Now does anybody have any idea if there is some kind of reference which list all lisp functions macro's etc?

Thanks for all the reply's,

Tim

---

### Post by CptPicard on 2008-06-15
Simple answer without going to any details; use a combination of SBCL and Emacs and SLIME for the IDE. You really really want the dynamic programming environment, it's more than half the fun and profit of using Lisp in the first place.

I'll ask Lars for his quickstart guide the link of which I've lost, moment... --> [http://common-lisp.net/~lnostdal/writings/sbcl.html](http://common-lisp.net/~lnostdal/writings/sbcl.html)

---

### Post by Timdejager on 2008-06-15
I've found [http://www.lispworks.com/documentation/HyperSpec/Front/index.htm](http://www.lispworks.com/documentation/HyperSpec/Front/index.htm)
and
[http://www.lispdoc.com/](http://www.lispdoc.com/)

as a reference, quite nice :)

---

### Post by maximinus_uk on 2008-06-16
> **CptPicard said:**
> Simple answer without going to any details; use a combination of SBCL and Emacs and SLIME for the IDE. You really really want the dynamic programming environment, it's more than half the fun and profit of using Lisp in the first place.

While I couldn't agree more on the dynamic programming enviroment, Emacs + SLIME are not the only option: Eclipse + CUSP comes with a REPL and a LISP aware enviroment. It's also easy to set up and friendlier than Emacs.

I must admit to being an Emacs fan but to be honest it's a real voyage for the first year as you learn to tame the beast. It's hard enough to get up to speed in Lisp for the first time without having to learn a whole new editing experience :)

---

