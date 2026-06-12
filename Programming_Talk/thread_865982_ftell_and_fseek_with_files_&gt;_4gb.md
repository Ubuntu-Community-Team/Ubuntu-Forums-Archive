---
title: "ftell and fseek with files &gt; 4gb"
date: 2008-07-21
forum: Programming Talk
---

### Post by unoodles on 2008-07-21
Does anyone know of a way to use ftell() and fseek() on files that are greater than 4gb? Or are there alternate functions that work?

Thanks in advance.

---

### Post by Zugzwang on 2008-07-21
You need to use "ftello" and "fseeko" for that.

See [here]("http://ac-archive.sourceforge.net/largefile/use_off_t.html") for further reading.

---

### Post by unoodles on 2008-07-21
Thanks

---

