---
title: "How to join multiple binary files into one like copy /b in msdos"
date: 2006-11-09
forum: Programming Talk
---

### Post by Paloseco on 2006-11-09
In msdos you can do "copy /b part1 + part2 + part3 file.ext". How can this be done in linux?

---

### Post by Najand on 2006-11-09
Hmm... CAT command may do that...
```

cat part* > file.ext

```

---

### Post by Paloseco on 2006-11-09
ok thanks

---

### Post by Seine on 2006-11-09
IIRC there's a tool called **chunk** that seems to do the same.

chunk part.01 part.02 part.03 final

---

