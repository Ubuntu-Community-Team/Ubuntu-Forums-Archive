---
title: "Debugging in python."
date: 2007-05-15
forum: Programming Talk
---

### Post by kragen on 2007-05-15
I can't find a decent debugger for python - I've tried all the graphical debuggers I could find:

winpdb
ddd
xxgdb

But I've had various problems with just about all of them.

Are there any others out there that I've missed, or am I going to have to stick with a command line debugger like pydb?

---

### Post by gotgenes on 2007-06-02
I wrote a [tuturial on using Winpdb]("http://gotgenes.com/swcatvtwiki/DebuggingExercise") that may interest you.

---

### Post by ghostdog74 on 2007-06-02
> **kragen said:**
> 
Are there any others out there that I've missed
the pdb module is good enough. just import it, set a trace in your script, and then you can debug.

---

### Post by 56phil on 2007-06-03
Eric has a really nice debugger.

---

