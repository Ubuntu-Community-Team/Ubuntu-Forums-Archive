---
title: "Finding and deleting repeating text"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Mramius on 2008-05-14
I have figured out how to find repeating text in a file by using:

```
sort filename | uniq -d
```

How can I then delete the repeated lines?

---

### Post by joshsmith on 2008-05-14
perhaps the answer you really want it to only print the unique lines, ie using the -u option

---

### Post by Mramius on 2008-05-14
That will print them, yes.  But how do I remove them from the file?

---

### Post by joshsmith on 2008-05-14
using the -u option with give you the file but with only the non repeated lines, then you need to send this output into a file

you can send the output from any command into a file by doing >
ie 
echo "1" > file.txt

so just put
> path to file
at the end :)

---

