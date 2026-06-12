---
title: "diff: Argument list too long"
date: 2010-04-30
forum: Programming Talk
---

### Post by dragos2 on 2010-04-30
Hi friends, I need some help with this little script: it says argument list too long probably
because the awk outputs everything on one line.

```

diff $(awk '{print $8}' f1.txt) $(awk '{print $8}' f2.txt)

```

Neither this works:
```

a=$(awk '{print $8}' f1.txt)
b=$(awk '{print $8}' f2.txt)
diff "$a" "$b"

```

Any idea of how to fix this besides outputting those awks to separate files and diff from there ?

---

### Post by iponeverything on 2010-04-30
man diff:
> DIFF(1)                          User Commands                         DIFF(1)

NAME
       diff - compare files line by line


note the "compare files" part. As in two files.

---

### Post by dragos2 on 2010-04-30
> **iponeverything said:**
> man diff:


note the "compare files" part. As in two files.

Ups, I did not knew that. Thanks

---

