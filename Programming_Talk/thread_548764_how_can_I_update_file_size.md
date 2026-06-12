---
title: "how can I update file size"
date: 2007-09-11
forum: Programming Talk
---

### Post by Firippu on 2007-09-11
I want to delete some bytes out of a file but when I do it with a hex editor I get a size error.. I don't get this error when I fill the bytes with spaces.. but I don't want the useless 20202020 blah blah in the file. can somebody direct me to a windows or linux program to update the file size?

---

### Post by pmasiar on 2007-09-11
you cannot just go and update file size - what you should do is read the file and write needed part of it (with different name), then rename it.

Python is great for this kind of file shuffling, IMHO

---

### Post by Firippu on 2007-09-11
I had a program once for linux that did the job but now i can't find it and I don't know the name. it was a hex editor and when I saved the file it said "update file size? YES or NO".. or something like that.. O.o

---

