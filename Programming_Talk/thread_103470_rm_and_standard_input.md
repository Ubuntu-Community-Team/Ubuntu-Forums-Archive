---
title: "rm and standard input?"
date: 2005-12-14
forum: Programming Talk
---

### Post by kingmob on 2005-12-14
Ok, this is a simple question, but i couldn't find any other place to ask it, so here goes.
I'm trying to do this:
```

grep -l "OBJECT  = 'SKY     '" *.fits | rm -f

```
It's important that this works and that i can also do this with cp and move. Problem is that rm doesn't seem to accept the standard input from the pipe? Only sollution i found was a script i could not run, as i cannot be root on this system (it's on the university).
I suspect the sollution is very simple, but i'm just not that big a hero in the bash enviroment.

[edit]
And as always i find the answer while asking it :ashamed:
for completenes, i've use:
```

grep -l "OBJECT  = 'SKY     '" *.fits | xargs rm

```

---

