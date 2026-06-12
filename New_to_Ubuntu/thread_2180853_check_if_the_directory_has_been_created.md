---
title: "check if the directory has been created"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by Muhammad_Mudassir on 2013-10-14
i have created a directory and file by using terminal.
how i will check if the directory and file has been created?

---

### Post by VMC on 2013-10-14
using the 'ls' command. List the directory in question. For example:
ls /home/user/NewDirectory. If it has a space you need to wrap in quotes. Like so:
```
ls '/home/user/New Directory Created'
```

---

### Post by Muhammad_Mudassir on 2013-10-14
thanks

---

### Post by Bashing-om on 2013-10-14
Muhammad_Mudassir; Hi !

The "list" command will give that information.
as in for example
```

ls

```
will list all directories and files at the Present Working Directory
```

ls -la

```
gives a Long list of All files/direcories
```

ls -la <path> directory | file
##examples:
ls -la /var/log
ls -la /var/log/Xorg.0.log

```

see: in terminal command
```

man ls

```
[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by sammiev on 2013-10-14
You can "cd /{path to the directory you created}" from terminal.
"dir" to list the files.
All commands without the ""
You can also use the icon files and move to the directory you created and view the files within.

---

