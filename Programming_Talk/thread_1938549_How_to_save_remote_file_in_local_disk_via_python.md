---
title: "How to save remote file in local disk via python ?"
date: 2012-03-09
forum: Programming Talk
---

### Post by prismctg on 2012-03-09
how can i save [http://example.com/ex.jpg](http://example.com/ex.jpg) file in harddisk via python script ?

---

### Post by Tony Flury on 2012-03-10
look at wget - i would use that.

Or maybe the htmllib library if you insist on a pure python (wget is a command line tool).

---

### Post by codemaniac on 2012-03-10
> **prismctg said:**
> how can i save [http://example.com/ex.jpg](http://example.com/ex.jpg) file in harddisk via python script ?

Something like below all you want ?

```
import os 
print os.system('wget -c http://example.com/ex.jpg') 
```

os.system gives return code of the commnad .

---

### Post by prismctg on 2012-03-10
thnx a lot : codemaniac & Tony Flury :)

---

