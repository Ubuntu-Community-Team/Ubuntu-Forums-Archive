---
title: "Shell command for extraction"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by SteelCore on 2008-08-13
What is the shell command to extract a tar.bz2 file (currently on my desktop) to another location (in my case (/usr/share/stardict/dic)
I'm actually asking this coz I wasn't able to graphically copy and paste the extracted file into the mentioned directory. Got a message saying I don't have permission. So I thought it might be easier to do this using the shell  right after 'sudo su'. Please correct me if I'm wrong. Thanks

---

### Post by null byte on 2008-08-13
```
sudo tar xjvf archive.tar.bz2 -C /home/user/folder/you/want
```

---

### Post by finer recliner on 2008-08-13
it is not recommended to launch a GUI (graphic user interface) as root. instead, use:
```
gksudo nautilus
``` (for gnome environment)

i dont believe you can extract an archive to a location other then your current directory using tar

if you still want to use the command line, use this command to extract your .tar.bz2 archive:
```
 tar -xvjf archive.tar.bz2 
```

see tar's man page for more info

---

### Post by SteelCore on 2008-08-13
> **null byte said:**
> ```
sudo tar xjvf archive.tar.bz2 -C /home/user/folder/you/want
```

That did work.  Stardict is now fully operational.

---

### Post by Oldsoldier2003 on 2008-08-13
> **SteelCore said:**
> That did work.  Stardict is now fully operational.

Glad the folks here could be of help to you. If you need any more assistance please post again :)

---

### Post by scorp123 on 2008-08-13
> **finer recliner said:**
>  i dont believe you can extract an archive to a location other then your current directory using tar That's what the "-C" parameter is for ;)  See "null byte's" posting above.

---

### Post by hrod beraht on 2008-08-13
> **scorp123 said:**
> That's what the "-C" parameter is for ;)  See "null byte's" posting above.

-C means *change to directory*.

*man tar* will give more details on the available options.

Bob

---

### Post by scorp123 on 2008-08-14
> **hrod beraht said:**
> -C means *change to directory*.
*man tar* will give more details on the available options.  Exactly what I said. You probably quoted the wrong posting?? :confused:

Never mind.

---

