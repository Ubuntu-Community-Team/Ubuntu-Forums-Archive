---
title: "bash: why does this not work?"
date: 2007-03-07
forum: Programming Talk
---

### Post by newbie22 on 2007-03-07
```
if [ -f *rc ]; then echo true; else echo false; fi
```
Why does this not work even though there is a *rc file?

---

### Post by Ramses de Norre on 2007-03-07
Try this:```
for i in *rc
do
    if [ -f $i ]
    then
        echo true
    else
        echo false
    fi
done
```

EDIT: forgot a '$' as pointed out ;)

---

### Post by duff on 2007-03-07
^^^ if [ -f $i ] ^^^

---

### Post by cwaldbieser on 2007-03-08
> **newbie22 said:**
> ```
if [ -f *rc ]; then echo true; else echo false; fi
```
Why does this not work even though there is a *rc file?

Because the shell first expands *rc to the actual filenames, so you end up with something like:
```

if [ -f onerc tworc threerc ]; then echo true; else echo false; fi

```
That syntax doesn't make sense, so you probably get "bash: [: too many arguments".

---

### Post by Mr. C. on 2007-03-08
See "man test" and search for -f and friends.  Get clear in your mind what FILE means.

MrC

---

