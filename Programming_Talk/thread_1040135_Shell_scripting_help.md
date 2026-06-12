---
title: "Shell scripting help"
date: 2009-01-15
forum: Programming Talk
---

### Post by DFord425 on 2009-01-15
I have a problem that i cant really figure out. I need to make a list of files, but only the files owned by root. so in my script, i use the command:
```
ls -la | grep root > $root_files
```
So now i have a file of all the entries owned by root. But i want just the file names, not the permissions, ownerid, groupid and the rest of the stuff you get from using the -l flag. How can i parse this so that i take the file names and put them into another file?

---

### Post by x22 on 2009-01-15
try using "cut" like so:

 ls -la | grep root |cut -b 50-80

---

### Post by DFord425 on 2009-01-15
Thanks for the help, i will read up on the cut command.

---

### Post by stylishpants on 2009-01-15
```
find .  -maxdepth 1 -type f -user root
```

---

### Post by Cracauer on 2009-01-15
Using find is obviously better, but just for completeness, your original code gives you file that have "root" in the name and are not owned by root.

A better solution ignoring find would look like this:
```

ls -lda "$@" | awk '$3 == "root" {print}'

```

But note that this also gives you ".." in many directories which almost certainly is not what you want. Again, using find avoids the problem.

---

