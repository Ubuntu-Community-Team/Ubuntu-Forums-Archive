---
title: "run commands one by one in the same console string"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-11
Hi all, 

how do I run commands one by one in the same console string? 
What I mean... 

For example, my need is to run two commands: 

# ls /home/user > files.txt 
# wput ... (put file into remote ftp directory) 

How do I perform these two commands in one string? Is it possible at all?

---

### Post by codemaniac on 2013-02-11
using the "&&" operator?

---

### Post by nothingspecial on 2013-02-11
```
command 1 ; command 2
```

or


Press Ctrl-X then Ctrl-E, type them all in there, one line at a time, then press Ctrl-O then Enter then Ctrl-X

There are other ways too based on conditionals && and ||

---

### Post by mcduck on 2013-02-11
...and it should probably be added that each of these wasy works differently, so pick one depending on what you want to do:

This runs command1, and after that command2:
```
command1 ; command 2
```

This runs command1, and only *if it completes succesfully*, command2:
```
command1 && command 2
```

...and this runs command1, and i*f it fails*, then command2:
```
command1 || command 2
```

---

### Post by Jibril00 on 2013-02-11
```
ls /home/user > files.txt && wput ... (put file into remote ftp directory)
```

That's it.

---

