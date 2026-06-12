---
title: "bash: if fail, then exit code"
date: 2007-03-19
forum: Programming Talk
---

### Post by newbie22 on 2007-03-19
```
if [ $1 = "" ]; then echo "fail"; exit 0; fi
```
The code needs a $1 entry in order to work.  Without it, the code will just blur out errors.  If failed to provide a $1 entry, I want the script to exit instead of blurring out the errors.

What needs fixing in the above code?

---

### Post by cwaldbieser on 2007-03-19
> **newbie22 said:**
> ```
if [ $1 = "" ]; then echo "fail"; exit 0; fi
```
The code needs a $1 entry in order to work.  Without it, the code will just blur out errors.  If failed to provide a $1 entry, I want the script to exit instead of blurring out the errors.

What needs fixing in the above code?

```

if [ -z "$1" ]; then echo "fail"; exit 0; fi

```
Try "man test" or "man [" for more info on the types of tests you can do.

---

### Post by Jussi Kukkonen on 2007-03-19
An non-existing variable is not the same as "". You can bypass this with a trick:
```
if [ x$1 = x"" ]; then 
  echo "fail"; 
  exit 0; 
fi
```

cwaldbiesers suggestion is better in this case, but my code works even if you actually wanted to compare to something:
*if [ x$1 = x$COMP_VAR ]; *

---

