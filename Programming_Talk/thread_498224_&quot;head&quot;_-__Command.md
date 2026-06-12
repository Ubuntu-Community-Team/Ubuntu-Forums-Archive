---
title: "&quot;head&quot; -  Command"
date: 2007-07-11
forum: Programming Talk
---

### Post by zoobave on 2007-07-11
Hi,
         I want to print a file from 25th line to till the EOF. How can i use the "head"  or "tail" or similar commands?

Regards
Zoobave
[http://zoobave.blogspot.com/]("http://zoobave.blogspot.com/")

---

### Post by jyba on 2007-07-11
I usually use sed for something like this.
```
sed 1,24d FILENAME
```

---

### Post by vaibhav on 2007-07-11
Try using awk..
```
awk '{if (NR>24) print;}' input.txt
```

(Above code is untested.)

---

### Post by ghostdog74 on 2007-07-11
```

awk 'NR>24' "file"

```

---

### Post by quux on 2007-07-11
Let me add one more...
```
tail -n +25 foo.txt
```

---

