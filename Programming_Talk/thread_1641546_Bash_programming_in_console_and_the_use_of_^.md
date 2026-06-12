---
title: "Bash programming in console and the use of ^"
date: 2010-12-09
forum: Programming Talk
---

### Post by khantastic on 2010-12-09
Hello

The use of ^ in bash is quite a nice feature, however my usage is limited and I would like to extend it.

```

ls file1.txt
^1^2 #same as 'ls file2.txt'

```

Line one in the above code do a simple ls of the file file1.txt. The second line executes the command in the first line by replacing 1 with 2. This works great.

Do anyone know if I can replace all occurrences of a string with a new one using the ^? Only the first match will be replaced while other matches are not updated. 
E.g. 
```

ls file1.txt file2.txt
^txt^py # actual: 'ls file1.py file2.txt' expected: 'ls file1.py file2.py'

```

Anyone know the syntax? Tried to google it but it doesn't handle ^ very well not giving me any good hits.

-SA

---

### Post by DaithiF on 2010-12-09
the ^ is a shortcut, to do a global replace you need the longhand version:
```
!!:gs/txt/py/

```no need to google, everything you need to know [COLOR=Red]about bash [/COLOR]is in [B]man bash

[/B]edit: [COLOR=Red]slight qualification[/COLOR]

---

