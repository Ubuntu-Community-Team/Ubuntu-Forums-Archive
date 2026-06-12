---
title: "get a specific line from a file Unix Shell Scripting"
date: 2010-04-27
forum: Programming Talk
---

### Post by hakermania on 2010-04-27
Hi, I know that this has been discussed again but I am still wondering how to get a line from a file.
I have a file named test.txt:
[B]user:hello
profile:blue
color:blue
true:0
false:1
[/B]What is the command to read the line 3 (color:blue) ?????

---

### Post by dragos2 on 2010-04-27
I think it can be achieved using many ways like
```

# print line number 52
 sed -n '52p'                 # method 1
 sed '52!d'                   # method 2
 sed '52q;d'                  # method 3, efficient on large files

```
from [http://www.linuxquestions.org/questions/linux-software-2/sed-display-text-on-specific-line-of-text-file-397405/](http://www.linuxquestions.org/questions/linux-software-2/sed-display-text-on-specific-line-of-text-file-397405/)

Also I think some like this (not tested and ugly)
cat file | awk 'NR>2 && NR<4{print $0}'

Also you can play with head and tail, etc.

---

### Post by hakermania on 2010-05-01
My friend I have to tell you that the last was the best solution!

---

