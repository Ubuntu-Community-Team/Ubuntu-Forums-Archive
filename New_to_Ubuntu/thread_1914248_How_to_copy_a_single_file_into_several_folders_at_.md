---
title: "How to copy a single file into several folders at a time"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by pavanmatham on 2012-01-24
Hi,

I am searching for a tool for _**copying**_ a same _**file**_ _**into several folders**_ _**at a time**_ instead of copy and paste several times.

Can any one suggest a way.... It will save lot of time.

Thanks.

Pavan

---

### Post by papibe on 2012-01-24
The easiest way would be to write a little bash script:
```
for dest in dir1 dir2 dir3; do
    cp -v source "$dest"
done
```
I hope it helps.
Regards.

---

