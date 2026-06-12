---
title: "Emacs term mode"
date: 2010-04-11
forum: Programming Talk
---

### Post by covertcj on 2010-04-11
Hi,

I was unsure exactly where to ask this, but I figure emacs is generally used in programming environments, so here it goes.

I've been using emacs a lot lately (and I'm loving it), and I find the terminal mode very convenient (M-X term). I am wondering if there is a way (a parameter to pass into the program upon starting it up or something) to start emacs with the terminal mode open. 

Thanks,
Chris

---

### Post by Cracauer on 2010-04-11
`emacs -f term`?

---

### Post by pbrane on 2010-04-11
**emacs -nw** in a terminal.

My bad, I misunderstood the question.

---

### Post by jpkotta on 2010-04-11
Looks like Cracauer already answered this, but I thought I'd mention multi-term.  It uses term-mode, but has (IMO) saner defaults and some handy extensions.  [http://www.emacswiki.org/emacs/MultiTerm](http://www.emacswiki.org/emacs/MultiTerm)

---

### Post by covertcj on 2010-04-12
Thanks, I guess I completely misunderstood the usage of the -f parameter before.

Also, MultiTerm looks great, thanks for the info!

Thanks again,
Chris

---

### Post by psusi on 2010-04-12
You can also add (term) to your ~/.emacs file.

---

