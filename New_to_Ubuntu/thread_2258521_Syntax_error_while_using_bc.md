---
title: "Syntax error while using bc"
date: 2014-12-28
forum: New to Ubuntu
---

### Post by black8 on 2014-12-28
Hey,

I am learning shell scipting. Thought that will be a good way to learn linux. I was trying bc command, and have a syntax error. I cant seem to find out why, and am sure you guys will know:

```
v2=`bc << eof
scale=4
v=3/4
$v*4
eof`
(standard_in) 3: syntax error


```

Thnaks!

---

### Post by spjackson on 2014-12-28
That should be
```

v*4

```

---

