---
title: "math with php/html?"
date: 2009-03-10
forum: Programming Talk
---

### Post by minsf on 2009-03-10
any of you gurus have any experience with quotients, roots and the like on html pages produced by a standard lamp install? i'd like php to generate the formula randomly, which is easy, except i cannot display it properly... my only success was with exponents using <sup> . my next idea is to try to generate roots graphically with php's gd, but i thought there may be a simple way to do it. surely, someone has tried this before me...
thanks for your help

---

### Post by svr2009wwe on 2009-03-10
Check [http://w3schools.com]("http://w3schools.com")

---

### Post by Tibuda on 2009-03-10
You should check MathML.

---

### Post by minsf on 2009-03-10
thanks a lot for the replies!

would you be able to be more specific about w3schools.com? i ran a few google searches with "site:w3schools.com" and couldnt find it there- would you be able to point me to the exact link there? thanks

as for MathML, this seems to be exactly what i need, except that it is not supported by a default installation of any browser i know (firefox, safari, etc)... guess is have to generate images of the formulae with some graphics.

---

### Post by minsf on 2009-03-10
correction: it actually does seem to work with firefox, but not with my safari, my cell phone, etc...
but at least firefox is something to start with

---

### Post by Tibuda on 2009-03-11
Yeah, only recent Gecko versions can render MathML. If you want a cross-browser solution, the best option is to generate PNG images from server-side. Here's a tutorial I found about using PHP to display LaTeX equations.

[http://www.linuxjournal.com/article/7870](http://www.linuxjournal.com/article/7870)

---

