---
title: "Read all lines that begin with a specific word Unix Scripting"
date: 2010-05-09
forum: Programming Talk
---

### Post by hakermania on 2010-05-09
Hi, i have a file and i want to read all lines that start with
<PassportName>
Any help?
thx!

---

### Post by soltanis on 2010-05-09
```

grep "<PassportName>" [file]

```

---

### Post by Portmanteaufu on 2010-05-09
> **soltanis said:**
> ```

grep "<PassportName>" [file]

```

Yup yup! Grep is your friend. However, if you only want lines that *start* with PassportName, you'll need to use:
```

grep '^PassportName' [file]

```
The leading carat (^) specifies that it should only print the line if PassportName's at the very beginning.

---

### Post by hakermania on 2010-05-12
Thank you VERY much!

---

