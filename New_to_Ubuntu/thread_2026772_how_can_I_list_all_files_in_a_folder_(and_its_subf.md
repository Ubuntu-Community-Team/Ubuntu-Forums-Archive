---
title: "how can I list all files in a folder (and its subfolders) in decreasing size order"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by hanzj on 2012-07-15
Hello,

What terminal command can I run that will list all files from largest file size to smallest, but with a minimum file size of 2 megabytes, and all files in  folder .mozilla and its subfolders only?

---

### Post by steeldriver on 2012-07-15
how about

```
find .mozilla -type f -size +2M -exec ls -hs {} \; | sort -hr
```

---

### Post by llamabr on 2012-07-15
> **steeldriver said:**
> 
```
find .mozilla -type f -size +2M -exec ls -hs {} \; | sort -hr
```
or:
```
find ~/.mozilla -type f -size +2M -exec ls -hs {} \; | sort -hr
```

---

