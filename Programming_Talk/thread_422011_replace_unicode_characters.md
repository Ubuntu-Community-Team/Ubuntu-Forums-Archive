---
title: "replace unicode characters"
date: 2007-04-24
forum: Programming Talk
---

### Post by ryu kun on 2007-04-24
I want to write a simple program to replace some unicode characters to others.

What I want to do is to replace these characters in a given text file:

ý  --> &#305; or i
ð --> &#287; or g
þ --> &#351; or s

Source text file's encoding may vary. The target text file can be UTF-8.

Could you please guide me, how can I do this in Python or C or Pascal?

---

### Post by Nikron on 2007-04-24
It'd be something like in python
```

f = open('filetobeopend','r')
w = open('filetowrite','w')
for line in f.readlines():
   w.write(line.encode('utf-8').replace('ý','i'))

f.close()
w.close()

```

Just look up file read/write and string manipulation at [www.python.org](www.python.org) in the tutorials

---

