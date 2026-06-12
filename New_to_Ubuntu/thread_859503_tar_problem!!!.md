---
title: "tar problem!!!"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by raedbenz on 2008-07-14
Hi,,i get this error, y??

```
root@raed-laptop:/# tar -xjf /cs-e9302_root2.tar.gz
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

```
thanks

---

### Post by Dr Small on 2008-07-14
Try:
```
tar -xvf /cs-e9302_root2.tar.gz
```

---

