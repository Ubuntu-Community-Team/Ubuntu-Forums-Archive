---
title: "Easy python question"
date: 2013-02-01
forum: Programming Talk
---

### Post by Spae on 2013-02-01
I started learning python a few days ago.

The input operator will work in IDLE (v3.3) but not if i use the same code in a .py within the terminal.

For example:
```
a = input("type anything")
print(a)
```

```
type anything ok
Traceback (most recent call last):
  File "p.py", line 1, in <module>
    a = input("type anything ")
  File "<string>", line 1, in <module>
NameError: name 'ok' is not defined
```

---

### Post by memilanuk on 2013-02-02
Just a wild guess... when you are running IDLE 3.3, you are running Python 3.x.  When you just enter 'python' at the command line in the Terminal app... does it say something like 'Python 2.x.x'?

You can either run the same version of Python as IDLE 3.3 is using by typing 'python3' instead of 'python', and your code should work as is.

If you want to use python 2.x, the command would be:

```
a = raw_input("Type anything")
```

---

### Post by Spae on 2013-02-02
Thank you for reply!
I will type python3 from now on:)

---

