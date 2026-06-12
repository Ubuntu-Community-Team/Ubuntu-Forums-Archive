---
title: "fyi only - ipython"
date: 2008-11-25
forum: Programming Talk
---

### Post by glok_twen on 2008-11-25
(i am not in any way connected with any sort of dev or formal promotion of this... just found it today and noting how helpful it can be if you have not used it yet)

have you used this shell before? i am nominating it for one of the best things since sliced bread.

sure there are many python shells, but this one takes it to a whole new level:

- tab lookups on any command - much better than any python ide i've tried
- integrated shell and python code dev
- seamlessly switch between line and screen editors
- ability to get the same common benefits of the python shell such as experimenting with commands
- tab look up on import modules too - try import o<tab>

it is really cool and worth an hour to get the basics.

---

### Post by slavik on 2008-11-25
well, I don't know about the best thing since sliced bread ;) but it is noteworthy :)

---

### Post by jacensolo on 2008-11-25
I tried it, but didn't see what was so great about it. The import <tab> thing is pretty cool though.

---

### Post by Greyed on 2008-11-26
I dunno, it would be pretty hard to beat WingIDE code completion.  The best feature is the Source Assistant.  It shows you the definition and Doc string of the current function/method *including any you've written for your current project*.

---

### Post by glok_twen on 2008-11-26
rationale - a recent and more comprehensive list of pluses:
[http://personalpages.tds.net/~kent37/kk/00011.html](http://personalpages.tds.net/~kent37/kk/00011.html)


good cheat cheats:
[http://www.dugthawts.com/wp-content/uploads/2008/08/ipython-cheat-sheet.txt](http://www.dugthawts.com/wp-content/uploads/2008/08/ipython-cheat-sheet.txt)
[http://pages.physics.cornell.edu/~myers/teaching/ComputationalMethods/python/ipython.html](http://pages.physics.cornell.edu/~myers/teaching/ComputationalMethods/python/ipython.html)

---

### Post by Endolith on 2008-12-30
> **glok_twen said:**
> 
- tab look up on import modules too - try import o<tab>

Why doesn't this work with certain modules (like matplotlib)?

---

### Post by iQuizzle on 2008-12-31
i use it all the time :P

it's very helpful..and i'm a sucker for the colors rather than the plain black in the regular python shell.

---

### Post by aranke on 2009-01-01
I prefer the default Python shell though I use iPython to look up various Matplotlib functions.

---

### Post by Endolith on 2009-01-09
> **Endolith said:**
> Why doesn't this work with certain modules (like matplotlib)?

I found the reason.  When I first did this on another machine it printed > please wait ( this will only be done once - %rehashx to regenerate)Indeed, the modules it wasn't completing were installed after it generated the list.   %rehashx regenerates the tab-completion for modules so they are all included now.

---

### Post by Endolith on 2009-01-09
> **aranke said:**
> I prefer the default Python shell though I use iPython to look up various Matplotlib functions.

Why?  Doesn't IPython do everything the regular shell does and more?

---

