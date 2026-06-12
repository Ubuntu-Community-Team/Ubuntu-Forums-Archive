---
title: "remove first line from file"
date: 2007-03-28
forum: Programming Talk
---

### Post by monkeyking on 2007-03-28
Is there some nice linux tool for removing the first line of a file?

thanks in advance

---

### Post by Ragazzo on 2007-03-28
One way: **sed 1d file > newfile**

---

### Post by monkeyking on 2007-03-28
hehe thanks for the quick reply

---

### Post by &lt;mawe&gt; on 2007-03-28
Another way: **tail +2 file > newfile**

---

### Post by rumli on 2008-12-30
> **<mawe> said:**
> Another way: **tail +2 file > newfile**

I think it should be ```
tail **-n** +2 file > newfile
```

---

