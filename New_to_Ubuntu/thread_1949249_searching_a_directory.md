---
title: "searching a directory"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by chemjeff on 2012-03-29
Hi,
I have a large directory and I want to find a file somewhere in it that has certain letters in the filename.  How can I go about searching for it?  Thanks!

---

### Post by codemaniac on 2012-03-29
In order to search a file by name in a directory you can use the "find" command like below .
```
find full_path_to_directory -name "filenamepatterrm*" -print
```

---

### Post by codemaniac on 2012-03-29
You can also check out manual pages of find to have more information .

---

### Post by chemjeff on 2012-03-30
Thanks!  But the manual page for find is very terse.  Is there a tutorial?

---

### Post by codemaniac on 2012-03-30
If you want to search a file with name only then you may refer to the command line mentioned in my earlier post #2 .

---

