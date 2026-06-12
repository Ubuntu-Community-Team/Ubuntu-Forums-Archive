---
title: "sed and append to everyline"
date: 2009-05-18
forum: Programming Talk
---

### Post by meg23 on 2009-05-18
How do you use sed to append a word to everyline of a text file? I cannot figure it out for the life me.

---

### Post by kaibob on 2009-05-18
I believe both of the following will work:

```
awk '{ print $0 "word" }' file > newfile
```

```
sed 's/$/word/' file > newfile
```

---

### Post by ghostdog74 on 2009-05-19
i see that you are messing around with Python in your recent posts. why don't you do it in Python then. To append to line, its just a matter of putting the new word at the end of the line
```

for line in open("file"):
  print line.strip(), "new word"

```

---

