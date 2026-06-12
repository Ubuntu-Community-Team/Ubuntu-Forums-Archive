---
title: "compare binary files"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by yc2 on 2008-05-18
Hello,
I have accidentally downloaded two package-archive-files that I think are just identical. How do i verify this before I delete one of them?
Thanks

---

### Post by hyper_ch on 2008-05-18
try: diff

---

### Post by yc2 on 2008-05-18
Thanks,
I HAD read the man diff, but it spoke a lot about lines and I wasn't sure it was OK for binary.
I just ran
```
diff file1.tar.gz file2.tar.gz
```
it gave no output, so I guess the files are the same?
Thanks.

---

### Post by kellemes on 2008-05-18
> **yc2 said:**
> 
it gave no output, so I guess the files are the same?

correct.

---

