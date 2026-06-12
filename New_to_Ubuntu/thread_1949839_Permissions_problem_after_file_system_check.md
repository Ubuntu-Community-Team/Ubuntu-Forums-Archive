---
title: "Permissions problem after file system check"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2012-03-31
I got a message saying the file system hadn't been checked in 24 boots, so I guess Ubuntu performed a file system check, but after it finished and booted into Gnome, I seem to be having alot of permissions issues like not being able to write to a folder, etc.

Anyone know what might have happened and/or if there is a solution?

---

### Post by santosh83 on 2012-03-31
> **Learning Linux 2011 said:**
> I got a message saying the file system hadn't been checked in 24 boots, so I guess Ubuntu performed a file system check, but after it finished and booted into Gnome, I seem to be having alot of permissions issues like not being able to write to a folder, etc.

Anyone know what might have happened and/or if there is a solution?

Can you give more details? Did you get any errors from fsck when it checked your filesystem? Did you try looking at 
```
$ dmesg | less
```
and
```
$ cat /var/log/syslog | tail -n 100 | less
```
and the log files in /var/log/fsck?

Try forcing another filesystem check by issuing
```
$ sudo shutdown -rF now
```

and see if any more errors or reported and if problems persist.

---

