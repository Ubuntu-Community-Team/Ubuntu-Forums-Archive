---
title: "Python 3.0"
date: 2009-06-13
forum: Programming Talk
---

### Post by riminicat on 2009-06-13
I decided to learn to program and would like to start with python 3.0, I have it installed on my system but when I run python in the terminal, the old version starts(because that was installed too).  How can I change it so that when I type "python", 3.0 is the one it uses?

---

### Post by simeon87 on 2009-06-13
Type:

```
which python
```

(on my system: /usr/bin/python)

and change/replace that link by a link to python3.0. So in other words, create a link to the python3.0 executable and put it there as python.

---

### Post by riminicat on 2009-06-13
Hey thanks, that was simpler than I imagined.

---

### Post by soltanis on 2009-06-13
Don't change that link. You might break other programs (which are python2.x scripts not compatible with python3) that depend on older python to run.

Instead, type 'python3' to get the 3.0.1 interpreter.

---

### Post by simeon87 on 2009-06-13
> **soltanis said:**
> Don't change that link. You might break other programs (which are python2.x scripts not compatible with python3) that depend on older python to run.

Instead, type 'python3' to get the 3.0.1 interpreter.

Good point.

---

### Post by Can+~ on 2009-06-13
```
python3 myscript.py
```

And if you want to define the typical header:

```
#!/usr/bin/python3
```

---

### Post by riminicat on 2009-06-13
Hey thanks guys, I'll do that.

---

### Post by jayboe on 2011-04-16
> **soltanis said:**
> Don't change that link. You might break other programs (which are python2.x scripts not compatible with python3) that depend on older python to run.

Instead, type 'python3' to get the 3.0.1 interpreter.

When I typed python3 in the terminal it did not work for me on  UE2.9(Ubuntu10.10), but when I appended the .0 (python3 now python3.0)  it worked fine. Thanks for the lead :smile:

---

### Post by cguy on 2011-04-16
even better: python3.1

---

