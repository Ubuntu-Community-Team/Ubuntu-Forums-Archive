---
title: "Looping out lines."
date: 2005-06-07
forum: Programming Talk
---

### Post by Zyko on 2005-06-07
Hi!

I have searched all day for a way to find out how to loop out each line in a document.

for example:

lines.txt:
Line 1
Line 2
Line 3

and i want a string to be set for each row in the document

 

So this would set

(Loop nr1)
line=Line 1
(Loop nr2)
line=Line 2


and so on...

Does anyone know?

---

### Post by LordHunter317 on 2005-06-07
Kind of hard to even suggest a solution when you don't specify what language.

---

### Post by Zyko on 2005-06-07
oh, i'm sorry.. its sh .. /bin/sh

---

### Post by LordHunter317 on 2005-06-07
```
cat /example.txt | while read line ; do
   # commands go here, line is in $line
done
```

---

### Post by Zyko on 2005-06-07
Ty so much, you just made my day :)

---

