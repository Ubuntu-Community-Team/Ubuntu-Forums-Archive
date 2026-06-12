---
title: "Bash script - can't open *.sh"
date: 2008-06-01
forum: Programming Talk
---

### Post by coombesy on 2008-06-01
Hi,

trying to write a bash script to clean up my desktop. Learning bash scripting passed two days, so solution might be obvious.

del_Torrents.sh
```
#!/bin/bash

rm -r ./*.torrent
```

(gonna start of simple) My 1st problem is that when i run:

coombes@coombes-laptop:~/Desktop$sudo sh del_Torrents.sh

i get:

sh: Can't open del_Torrents.sh

I did get this to work yesterday, after a few attempts. But today it's not! any ideas would be helpful.
Cheers.

---

### Post by ifross on 2008-06-01
Have you made the script excecutable?

[PHP]chmod a+x del_torrents.sh[/PHP]

---

### Post by geirha on 2008-06-01
> **coombesy said:**
> 
sh: Can't open del_Torrents.sh

That error message means it can't find the file. Are you sure the file is still there, and you typed the name correct? (remember, linux is case sensitive)

---

### Post by Majorix on 2008-06-01
Why don't you just use the terminal for this?

---

### Post by dje on 2008-06-01
Try this (make sure you are in the correct directory where the script is):
```
sudo ./del_Torrents.sh
```
You need the './' in front of the script because it isn't in the PATH variable

hope that helps,
dje

---

### Post by Prospero2006 on 2008-06-01
You Could:

Chmod the script as mentioned above.
Copy it to /usr/local/bin/
Type del_tor(tab)

or

Create an Alias

---

### Post by stroyan on 2008-06-01
> **ifross said:**
> Have you made the script excecutable?

[PHP]chmod a+x del_torrents.sh[/PHP]

If started with "sudo sh del_Torrents.sh" the file does not actually
need to be executable
[QUOTE=dje]
You need the './' in front of the script because it isn't in the PATH variable
[/QUOTE]

If started with "sh del_Torrents.sh" the file does not actually need to
be executable.  It only needs to be readable.  It also does not need to
be in a directory in $PATH, as long at it is in the current directory.
Both of those requirements do apply for running a script by name without
any explicit sh or bash command.

I favor the case-sensitive typo theory, or being in a different directory
than the del_Torrents.sh file.  The same error message could come from a
permissions problem if the file is present but not readable.  But running
sh with sudo will make any existing file readable to that sh.

---

