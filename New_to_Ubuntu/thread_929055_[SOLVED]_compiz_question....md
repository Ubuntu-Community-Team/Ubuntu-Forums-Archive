---
title: "[SOLVED] compiz question..."
date: 2008-09-24
forum: New to Ubuntu
---

### Post by fignig on 2008-09-24
so i'm wondering what is the easiest way to setup a script or something that will turn off compiz when i want, and turn it back on when i want. or is there some code to put in the terminal? i've been looking for one to turn it off, is like:
metacity --replace

or something like that, but i haven't found one to turn it back on when i want it back. b/c some of the games dont really work w/ it on, and i've been wanting to test them out, but not wanting to mess up my compiz.

---

### Post by knix on 2008-09-24
install fusion-icon in synaptic or with apt. You can add it to your session if you wish. You just click it to turn on/off.
or, for manual on/off, use compiz --replace.

---

### Post by fignig on 2008-09-25
> **knix said:**
> install fusion-icon in synaptic or with apt. You can add it to your session if you wish. You just click it to turn on/off.
or, for manual on/off, use compiz --replace.

will it keep my settings?

---

### Post by wolterh on 2008-09-25
You could code an application that would check if compiz is running. 
If it is, send 'killall compiz' to the terminal. If it is not, send 'compiz' to the terminal (in order to start it)

Anyway, why do you want to do it?

---

### Post by Beth1957 on 2008-09-25
> **fignig said:**
> so i'm wondering what is the easiest way to setup a script or something that will turn off compiz when i want, and turn it back on when i want.

There's a program called [Compiz-Switch]("http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on") which does just this. I've been using it for a while with no problems; it retains your compiz settings. You can make a launcher - I have mine on my task bar - and switch compiz on & off with one click. :D

---

### Post by fignig on 2008-09-25
> **Beth1957 said:**
> There's a program called [Compiz-Switch]("http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on") which does just this. I've been using it for a while with no problems; it retains your compiz settings. You can make a launcher - I have mine on my task bar - and switch compiz on & off with one click. :D

ty, that's exactly what i was looking for.

---

