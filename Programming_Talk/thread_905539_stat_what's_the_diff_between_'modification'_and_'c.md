---
title: "stat: what's the diff between 'modification' and 'change'?"
date: 2008-08-30
forum: Programming Talk
---

### Post by meganox on 2008-08-30
from man stat:

```
%x     Time of last access
%X     Time of last access as seconds since Epoch
%y     Time of last modification
%Y     Time of last modification as seconds since Epoch
%z     Time of last change
%Z     Time of last change as seconds since Epoch
```what's the difference between modification and change?

---

### Post by ghostdog74 on 2008-08-30
modification time is when the file data changed
last change time is when the meta data of the file changes, such as permissions and ownership

---

### Post by meganox on 2008-08-30
Thanks. I suspected as much but couldn't confirm.

Great Awk page in your sig too!

---

