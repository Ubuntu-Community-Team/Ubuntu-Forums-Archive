---
title: "Recursive Mass File Rename"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by The Titan on 2008-08-26
I got this command off of another site but it was an ancient thread so i thought i would just post it here


$ for i in *_*; do mv "$i" "`echo $i | tr '_' ' '`"; done
Anyone know how i can do this recursively?

---

### Post by -Zeus- on 2008-08-26
this will do it.

```
sudo find . -name *_* | while read FILE; do sudo mv "$FILE" "`echo "$FILE" | tr '_' ' '`"; done
```

---

