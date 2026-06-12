---
title: "How do I append a file to file in sed?"
date: 2007-09-11
forum: Programming Talk
---

### Post by PryGuy on 2007-09-11
I know it's a silly question, but it's pretty urgent for me... Please tell me how do I append a text file to the end of a text file in sed? Thank you!

---

### Post by aJayRoo on 2007-09-11
Does this need to use sed? This is what 'cat' (short for concatenate) is designed for:
```
cat file2 >> file1
```
Where 'file2' is appended to the end of 'file1'. For this type of operation cat is certainly the right tool for the job.

EDIT: Or if you do not wish to change the original files:
```
cat file1 file2 > newfile
```
which concatenates 'file1' and 'file2' and saves the result to 'newfile'.

---

