---
title: "grep \!"
date: 2009-04-16
forum: Programming Talk
---

### Post by ztrange on 2009-04-16
In the output of latex command, every error starts with \! so, I want to make something like

latex -halt-on-error 'file.tex' | grep \!

And get ony error output.

But it is failing and I don't know how to do it, I've tried several combinations of \\ and \!, appended ` to characters and used fgrep instead of grep but still cannot find the way to do it.

Can anybody help me?

Thanks

---

### Post by amauk on 2009-04-16
put the expression in single quotes, and escape the backslash
```
grep '\\!'
```

---

### Post by ostrm on 2009-04-16
Just a guess, but I think latex outputs errors to STDERR (can't check it now...), so redirecting to STDOUT could do the trick:
```
latex -halt-on-error 'file.tex' 2>&1 | grep '\\!'
```
with the correct escaping as given by amauk.

---

### Post by ztrange on 2009-04-17
Thanks for your help, 

I'm trying and right now, I'm almost done.

Where can I mak this as solved?? I can't find it

---

### Post by Tony Flury on 2009-04-17
You can't mark it as Solved (as per the old functionality), but you can add the "Solved" tag to the thread - which will help.

---

