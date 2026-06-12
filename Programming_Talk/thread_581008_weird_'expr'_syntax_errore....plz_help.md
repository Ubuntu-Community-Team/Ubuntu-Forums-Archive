---
title: "weird 'expr' syntax errore....plz help"
date: 2007-10-19
forum: Programming Talk
---

### Post by philip.yhelzon on 2007-10-19
I have a syntax errore in a command I'm trying to run....I don't see the problem :confused:

expr 0 `ls -l | grep '^-' | \
    sed 's/^\([^ ]*[ ]*\){4,4}\([0-9]*\).*$/ + \2/'`

What's wrong here?

I'm using the default Ubuntu shell (dash I think)
 


thanx

---

### Post by K.Mandla on 2007-10-26
Moved to Programming Talk.

---

### Post by nanotube on 2007-10-26
what are you trying to accomplish?

---

