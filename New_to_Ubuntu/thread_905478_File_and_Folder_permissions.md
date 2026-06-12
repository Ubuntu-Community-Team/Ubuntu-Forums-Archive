---
title: "File and Folder permissions"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by foofatron on 2008-08-30
I get denied accsess to the permissions of folders and the ability to copy and paste in like the bin. It won't let me change the permissions either. I'm on the root account too.

---

### Post by gmxgeek on 2008-08-30
what folder are you trying to change? can you cd to the folder and post
```

ls -l ../

```

---

### Post by drs305 on 2008-08-30
Just because you are the main user doesn't necessarily mean you are on the 'root' account. By default, even the first user normally does not have administrative powers unless he/she takes specific actions to do so.

For terminal commands, preface them with "sudo" as in "sudo cp thisfile /usr/bin"

To start gui-based apps, preface the start command with "gksudo" or "gksu" as in "gksudo nautilus".

When you invoke sudo/gksu, you will be asked for a password. As you type you won't see anything being entered but that is normal. Type your password and hit enter.

For more information about privileges, here are two links:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

If this post wasn't helpful please explain your situation a bit more fully.

Welcome to the ubuntu forums!

---

### Post by foofatron on 2008-08-30
I wanted to modify the gcc folder. I also can't copy in paste in the host folder either. I know about sudo, but I wanted to know if there were  copy commands and stuff or a way to set it so I can just move, copy, and paste without the terminal.

---

### Post by gmxgeek on 2008-08-30
the /usr/lib/gcc folder is under the root account, so as drs305 stated above, any modification to this folder must me run as the superuser using the sudo command.

---

### Post by foofatron on 2008-08-30
When I try sudo ls -l file /host/me 

error ls does not exist. Also is it possible to use folders with ' and spaces? It always ignores ' and spaces...

---

### Post by gmxgeek on 2008-08-30
try 
```

/bin/ls -l file

```

if that works then your $PATH variable is out of whack

[http://forums.macosxhints.com/archive/index.php/t-9795.html](http://forums.macosxhints.com/archive/index.php/t-9795.html)

and if you launch 
```

gksu nautilus

```

then you can have a gui that can move and copy and paste as root

---

### Post by foofatron on 2008-08-30
It doesn't work, but the gui does the job.

---

### Post by gmxgeek on 2008-08-30
if /bin/js doesn't work then you probably don't have it installed for whatever reason.

```

sudo apt-get install --reinstall coreutils

```

should get it back

---

### Post by gmxgeek on 2008-08-30
-

---

### Post by foofatron on 2008-08-30
I would, but unfortunately I can only connect with [windows]("http://ubuntuforums.org/showthread.php?t=905505").

---

### Post by cariboo on 2008-08-30
If file names with spaces are ignored use quote marks around the file or directory name eg:

```
ls -la "File with space in it"
```

you need to do the same for any command in a terminal.

Jim

---

