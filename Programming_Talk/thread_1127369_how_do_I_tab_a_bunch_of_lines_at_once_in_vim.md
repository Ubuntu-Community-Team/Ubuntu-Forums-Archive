---
title: "how do I tab a bunch of lines at once in vim?"
date: 2009-04-16
forum: Programming Talk
---

### Post by anonmars on 2009-04-16
I have a file like this:

```
while True:
   print "hello"
   print 1
   ...
```

If I were to insert an if statement above the "while True" how do I tab over the n lines below it in vim?  Doing it one line at a time takes too long if there are a lot of lines.

Thanks.

---

### Post by imdano on 2009-04-16
Use visual mode to select the whole block, then presss '>'.

---

### Post by anonmars on 2009-04-16
> **imdano said:**
> Use visual mode to select the whole block, then presss '>'.

Brilliant!  Thanks much!

---

