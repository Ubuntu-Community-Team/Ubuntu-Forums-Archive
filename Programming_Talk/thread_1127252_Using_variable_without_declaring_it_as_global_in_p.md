---
title: "Using variable without declaring it as global in procedure."
date: 2009-04-16
forum: Programming Talk
---

### Post by tusharv on 2009-04-16
Hi All,

In TCL if I want to use same variable in two diff. procedures then I have to define it as global in both procedures ?

If yes Then in my program I have around 50 variables and I want to used them in multiple procedures. then I have to define them global in all procedures?

Is there any other way ?

Thanks,
Tushar

---

### Post by nvteighen on 2009-04-16
Er... pass the needed variables as arguments. Declare them where needed and pass them around...

---

### Post by stevescripts on 2009-04-16
Sometimes, a global array or dict is really the right thing to do ...

Besides passing them around as nvteighen suggests (which is often the right thing), you  always have namespaces, uplevel and upvar at your disposal in tcl.

Steve

---

### Post by nvteighen on 2009-04-16
> **stevescripts said:**
> Sometimes, a global array or dict is really the right thing to do ...

Besides passing them around as nvteighen suggests (which is often the right thing), you  always have namespaces, uplevel and upvar at your disposal in tcl.

Steve
Well, I don't know Tcl so I couldn't think of namespaces and such... I just gave the generic advice valid for any decent programming language supporting procedures :)

---

### Post by stevescripts on 2009-04-16
FWIW, tcl's namespaces are quite similar to those of C++...

Your generic advice is pretty much right-on! ;)

---

