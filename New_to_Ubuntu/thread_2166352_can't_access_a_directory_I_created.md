---
title: "can't access a directory I created"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-08-08
Hello Everyone
                        I created a direrctory in my home directory. Yet I can't copy to it, it gives an error message , no such "file or directory". The directory shows up on a "ls" command, but it doesn't show up in Nautilus.  Helpppppppppppp.

Thank You

---

### Post by emerson1979 on 2013-08-08
the error tells me I can't change the contents of the folder

---

### Post by prodigy_ on 2013-08-08
> **emerson1979 said:**
> the error tells me I can't change the contents of the folder
Odd. What if you refresh (F5) or close and reopen Nautilus?

Are you trying to copy files via GUI or via command line? For the latter, keep in mind that file and folder names in Linux are case-sensitive.

---

### Post by Bashing-om on 2013-08-08
emerson1979;
Could be a number of causes...
Who owns that directory ?
```

ls -la <that-direcory-name>

```
example
> 
ls -la my-stuff

maybe there are spaces in the name ?
maybe there are capital letters in the name and you are using lower case letters ?

Can not say ..so provide to us what you are looking at with that "ls -la" command.


[INDENT][INDENT]more guidance to be provided
[/INDENT][/INDENT]

---

### Post by emerson1979 on 2013-08-09
the owner is root. So that seems to be the source of the problem. Thanks

---

### Post by Bashing-om on 2013-08-09
emerson1979; Hey,

You do good work ..must have created that directory while in the "super user" mode:
to change the ownership to yourself:
```

sudo chown <username>:<username> <directory>

```
example
> 
sudo chown sysop:sysop /home/sysop/my-stuff
where sysop is the "<username>" and the directory "my-stuff" is in your home directory ..in my case "sysop's".

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

