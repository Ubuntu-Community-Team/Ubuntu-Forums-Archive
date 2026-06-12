---
title: "'ls' command"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-09
With the 'ls' command I get the following result:

[I]drwx------  2 4096 2008-10-09 23:00 .
drwxrwxrwx 28 4096 2008-10-09 22:53 ..[/I]

What does the '2' and '28' mean, in each case just before 4096?
What does the '4096' mean?

---

### Post by ibuclaw on 2008-10-09
do you know what . and .. are?

. is a pointer to the current directory you are in
.. is a pointer to the directory above you in the filesystem tree

Now, as for the two numbers...

the first one is the hard link count, the second is the size of the directory in bytes.

ie:
```

d   rwx------ 2                 4096      2008-10-09 23:00
dir 7  0  0   hard link count   dir size  created/modified timestamp

```
To know what a hard link is... well, it is a pointer in the filesystem. Or, on a simpler level, a file.

Regards
Iain

---

### Post by SunnyRabbiera on 2008-10-09
ls is supposed to be the "list" command, if you were in a folder it would have given you the list of the contents of that said folder.
Running ls from the terminal though the menu wont do much, unless you give it a directory to scan.

---

### Post by ahsile on 2008-10-09
To be more specific... 2 is the number of hard links in the current directory ( . and .. ). 28 is the number of hard links in the folder one level above it. And, as a previous poster already stated 4096 is the size of the directory.

---

### Post by Primefalcon on 2008-10-09
to get an easier to read file size thing

try ls -l --si or ls -lh

I'd recomend the first though since that rounds the turn over points to 1000 instead of 1024 as is more the ratio used these days

---

