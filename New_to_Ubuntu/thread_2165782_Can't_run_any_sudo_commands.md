---
title: "Can't run any sudo commands"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by 8H3LnBH on 2013-08-06
Not sure what I am missing here but each time I try to run a command like "sudo <command>", it tells me "command not found.  If I do a dir from the folder I am in, the command I am trying to run is listed but it tells me it is not there.

---

### Post by Vladlenin5000 on 2013-08-06
Folders and files aren't commands... If you list the contents of a given folder that's most certainly what you're getting. However, just in case I'm not understanding your problem, post here exactly what you're trying to do, i.e., what commands you're actually trying to run.

---

### Post by steeldriver on 2013-08-06
If *command* is in a directory that is not in sudo's executable PATH, then you will need to give the path explicitly - in particular, if *command* is in your current directory, then that would be

```
sudo **./***command*
```

---

### Post by 8H3LnBH on 2013-08-06
> **steeldriver said:**
> If *command* is in a directory that is not in sudo's executable PATH, then you will need to give the path explicitly - in particular, if *command* is in your current directory, then that would be

```
sudo **./***command*
```

This solved my problem...thanks

---

