---
title: "Python - Invalid Syntax"
date: 2014-04-12
forum: Programming Talk
---

### Post by Yozuru on 2014-04-12
Hello everyone, I am still fairly new to python and I have received an invalid syntax error and i can't seem to resolve it at all. Here is a pastebin of my code: [HTML]http://pastebin.com/STc1FWCR[/HTML]

I am experiencing the error in line 4. Many thanks for any and all input.

---

### Post by steeldriver on 2014-04-12
Can I suggest you post short code fragments inline (between code tags) instead of posting a pastebin URL? 

Anyhow, it looks like you have an unmatched parenthesis (count 'em)

```

    parent = list**(**range**(**len**(**P**))**

```

---

### Post by Yozuru on 2014-04-12
Of course if it makes it easier to read!

```
def isPerm(P):
    count = 0
    perm = list(range(len(P)))
    for i in P:
        if i in perm:
            count += 1
        if count == len(i)
            return True
        else: return False
```

---

