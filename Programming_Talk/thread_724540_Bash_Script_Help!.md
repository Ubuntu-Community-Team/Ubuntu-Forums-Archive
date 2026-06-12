---
title: "Bash Script Help!"
date: 2008-03-14
forum: Programming Talk
---

### Post by oxsyn on 2008-03-14
I hope this is the correct plact to put this.  I've been playing with the CLI, trying to learn the ins & outs.  I can't seem to get the following command to work correctly:

> grep 'f4rr4r' /* 1>found.log 2>/dev/null &

I'm trying to search entire disk (in the background) for all files that contain my username (I know there are several on the filesystem).  I want to write the results to a file "found.log" and throw out the errors.

However, the process completes instantly & the found.log file is empty.
Any ideas?  Thanks!

---

### Post by Zwack on 2008-03-14
grep is not by itself recursive.  So your search is only searching /*

try

```
grep -R 'f4rr4r' /

```

If you only want the file names it was found in try grep -lR and if you want it case insensitive try grep -lRi ...

Z.

---

### Post by oxsyn on 2008-03-14
Ah, thank you. :)

---

### Post by mssever on 2008-03-14
The find command is intended for this purpose: ```
find / -name '*f4rr4r'
``` There are a lot of options to customize the behavior and output.

---

### Post by WW on 2008-03-14
> **mssever said:**
> The find command is intended for this purpose: ```
find / -name '*f4rr4r'
```

That command will look for f4rr4r in the file names.  If I understood the original poster correctly, he wants to search the *contents* of all the files.

---

### Post by mssever on 2008-03-14
> **WW said:**
> That command will look for f4rr4r in the file names.  If I understood the original poster correctly, he wants to search the *contents* of all the files.

My bad. I should have read the question a little more carefully.

---

