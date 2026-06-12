---
title: "open long named folders included space"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by REWENGER on 2008-05-21
hi.

i got a problem, i try to open a windows folder using the shell. when i try to open documents and settings it says cannot find file or folder /mnt/test/Documents.

---

### Post by N.N. on 2008-05-21
Enclose either the entire path or the part containing spaces in quotes ('), e.g. ```
cd /mnt/test/'Documents and Settings'/
```

---

### Post by hyper_ch on 2008-05-21
use TAB to complete file- and directory names... it will also make them automatically right with escaping ;)

---

### Post by Archmage on 2008-05-21
Insert:

cd /mnt/test/D

Than press the TAB-key (maybe twice). It will autocomplete the rest for you or you need to insert the o and do it again if you have more than one folder with D.

I think the right one would be

cd /mnt/test/Documents/ and/ Settings/

---

### Post by drs305 on 2008-05-21
actually, the spaces are escaped with a backslash. Documents and Settings would be Documents\ and\ Settings ... but the other ways, including tabbing, are easier

---

