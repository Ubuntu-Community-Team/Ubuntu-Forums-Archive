---
title: "[SOLVED] Add a fact iteractively in prolog?"
date: 2007-07-29
forum: Programming Talk
---

### Post by olejorgen on 2007-07-29
Silly question, but how do I add a fact interactively in prolog. ie. directly in the interpreter.

(swi-prolog)

---

### Post by pmasiar on 2007-07-29
[http://en.wikipedia.org/wiki/Prolog](http://en.wikipedia.org/wiki/Prolog)

Fact that you have cat, with name tom:

cat(tom).

---

### Post by olejorgen on 2007-08-10
```

?- cat(tom).
ERROR: Undefined procedure: cat/1

```

I suspect that it's somehow possible to change mode from "query" to "fact description" (?)

---

### Post by bigboy_pdb on 2007-08-10
Use assert.

So if you want to add the fact "cat(tom)." then use "assert(cat(tom)).". When you use the query "cat(tom).", Yes will be returned.

---

### Post by olejorgen on 2007-08-11
Thanks!

---

### Post by bigboy_pdb on 2007-08-11
You're welcome.

---

### Post by Syntaxius on 2007-09-30
An alternative, at leas in SICStus Proglog is:

?- [user]           %this loads an interactive "file" where you can give interactive commands direct to the promt. 
- cat(tom).
?- cat (tom).
- yes.

---

