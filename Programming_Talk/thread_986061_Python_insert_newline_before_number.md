---
title: "Python: insert newline before number"
date: 2008-11-18
forum: Programming Talk
---

### Post by Stefanie on 2008-11-18
I have a file and i need to insert a newline before every number ("2" --> "\n 2", "4" --"\n 4" and so on). 

I tried this in python:
```

import re

file = open("<path to file>", "r+")
content = file.read()
 
newlinesinserted = re.sub("([0-9])", "\n \1", content)

print newlinesinserted
```

When I execute this script the newlines are inserted properly but the numbers are replaced by question marks. does anybody know how to solve this?

---

### Post by ghostdog74 on 2008-11-18
how does your input file look like? and how would you want your output to look like?

---

### Post by WW on 2008-11-18
You need an extra backslash in front of \1 in the second argument of re.sub, otherwise \1 is handled as a special character before the argument is passed to re.sub():
```

newlinesinserted = re.sub("([0-9])", "\n \\1", content)

```

---

### Post by bobbocanfly on 2008-11-18
No need to use re, just us string.replace(). For example:

```
for i in range(0, 9):
    mystring = mystring.replace(str(i), "%s\n" % str(i))
```

---

### Post by Stefanie on 2008-11-19
thanks for your replies. i found out that inserting an r worked as well, but i don't know why:

```
newlinesinserted = re.sub(r"([0-9]+)", r"\n \1", content)
```

---

### Post by Greyed on 2008-11-19
The r works because that makes it a raw string.  Raw strings are not interpolated by Python, they are passed on without any changes.  Generally speaking you'll want to always construct regex with raw strings since the backslash (\) character is the escape for special characters in both Python and regex.

---

