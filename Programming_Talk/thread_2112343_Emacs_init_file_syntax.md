---
title: "Emacs init file syntax"
date: 2013-02-04
forum: Programming Talk
---

### Post by seeker.k3 on 2013-02-04
It's a dilemma: I want to be able to control emacs' start up and behaviour, but I haven't got time (or the desire, which is the same thing) delving into the dark waters of LISP code.

Some lines of my .emacs file start with a single quote,
```
'(blink-matching-paren nil)
```
and some do not.

Can someone please tell me when I need to start the line with a quote?
And what does it mean?
Also, can I add new lines anywhere, or is there an order? Is the section (custom-set-variables) necessary? And can type in my own lines there?

Thank you.

---

### Post by schauerlich on 2013-02-04
Well, if you really want to do much with your init file, you will need to learn a bit of emacs lisp. It's kind of unavoidable.

Now, as far as the meaning of that line, it's uncertain without context. A single quote proceeding something in parentheses is a "quoted expression" - that is, interpret that s-expression that is not evaluated, and instead is interpreted as a list literal. So, from the code you've provided there, someone made a list of two elements: the symbol "blink-patching-paren" and the atom "nil". However, by itself, this doesn't do much. It's possible that it's actually an argument to a function that's enclosing the expression, which you did not paste here. On it's own, it's like having the line '["blink-matching-paren", None]' on a line by itself in python - doesn't do much. Perhaps someone with a VB background thought they were commenting something out?

Order does matter, for the most part.

---

### Post by seeker.k3 on 2013-02-05
Ahh, yuk. You see, that's the problem. Emacs is fanastic software, but it comes with strings attached. Batteries aren't included.

Ok. Thank you for your answer. It's a very good answer, I think. 

Does anyone know when it will all end? Sorry for complaining; I love emacs, but I hate it to.

---

### Post by seeker.k3 on 2013-02-06
I've just learnt to debug it, a bit.
```
 $ emacs --debug-init
```
I've also just learnt that it's abbrevs in .emacs.d/ that is causing me problems, both at start up and shut down. Every time I set up an abbreviation in emacs, trouble. If I find out more, I'll put it here. Does anyone else have init problems when they use abbrevs, or is just me?

---

