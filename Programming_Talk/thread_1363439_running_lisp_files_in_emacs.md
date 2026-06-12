---
title: "running lisp files in emacs"
date: 2009-12-24
forum: Programming Talk
---

### Post by badperson on 2009-12-24
It seems to me I came across a web page explaining how to run lisp files in emacs...but now I can't find it. 

In other words, if I have a file called test.lsp and it contains this text: 
```
(+ 3 2)
```

how do I get that to output in emacs?
bp

---

### Post by unknownPoster on 2009-12-24
I think you're going to need to set up slime.

[http://common-lisp.net/project/slime/](http://common-lisp.net/project/slime/)

Here are some simple directions for installing it and getting it to run on Ubuntu:

[http://www.osix.net/modules/article/?id=912](http://www.osix.net/modules/article/?id=912)

---

### Post by tageiru on 2009-12-24
Emacs is itself a lisp interpreter.

Use ctrl-j after a form to evaluate it and insert the result in the buffer and ctrl-x ctrl-e to evaluate it without inserting.

---

