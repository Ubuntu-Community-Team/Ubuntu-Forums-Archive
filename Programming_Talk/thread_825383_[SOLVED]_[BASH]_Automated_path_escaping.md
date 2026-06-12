---
title: "[SOLVED] [BASH] Automated path escaping"
date: 2008-06-10
forum: Programming Talk
---

### Post by altonbr on 2008-06-10
So we all know that some people have spaces and other unwanted characters inside folder names, and that's all fine and dandy when tranversing through BASH because you can use auto completion, but if you piping multiple directories to, say 'tar', how do I escape these folder names so tar doesn't go looking for "My" and "Music" instead of "My\ Music"?

I tried wrapping each directory in quotes, but tar didn't seem to like it.

---

### Post by Phenax on 2008-06-10
```

$ echo "You can use sed, of course" | sed 's/ /\\ /g'
You\ can\ use\ sed,\ of\ course

```

---

### Post by altonbr on 2008-06-10
> **Phenax said:**
> ```

$ echo "You can use sed, of course" | sed 's/ /\\ /g'
You\ can\ use\ sed,\ of\ course

```

But there are 20 characters that should be escaped, is there not?

Such as:
> !() {}[]

---

### Post by Phenax on 2008-06-10
```

echo -n "[big fat friggin <messy> filename]" | xargs --null tar -cf archive.tar

```

---

### Post by altonbr on 2008-06-11
> **Phenax said:**
> ```

echo -n "[big fat friggin <messy> filename]" | xargs --null tar -cf archive.tar

```

What about multiple directories with spaces?

---

### Post by altonbr on 2008-10-26
According to [http://wooledge.org:8000/BashFAQ](http://wooledge.org:8000/BashFAQ), you can do it something like this: ```
find . -type f -print0 | xargs -0 grep -l "$search"

```
> The -print0 / -0 options ensure that any file name can be processed, even one containing blanks, TAB characters, or newlines. 

---

