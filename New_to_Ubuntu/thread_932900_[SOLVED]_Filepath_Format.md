---
title: "[SOLVED] Filepath Format?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by fgn89 on 2008-09-28
Hey. Just to state again, I've newly migrated here from windows.

Well, there's this program I'm using, when in Windows, it's only able to access databases, if I use the correct network path.

Right now, it just won't work on Ubuntu.

I've found out, through some testing on a windows platform, it wouldn't work if I set the path to the database in the following format.

\\(IP ADD)\(shared directory)\test.gdb

e.g \\192.168.0.3\database\test.gdb

But it works if I put it in the following format.

(IP Add): (drive):\database\test.gdb

e.g. 192.168.0.3: D:\database\test.gdb

**Ignore the spaces, they would make smileys otherwise**

I don't believe Ubuntu has anything like C, or D drives?

So I was just wondering how do I set the path in the format that works.

'cause, 

In FlameRobin Database Admin, it shows the file as..

[email]SYSDBA@localhost:/home/fgn89/Documents/database/TEST.GDB[/email] (NONE)

but if I set it to..

192.168.0.3:SYSDBA@localhost:/home/fgn89/Documents/database/TEST.GDB (NONE) 

It doesn't work.

Any tips?

---

### Post by louieb on 2008-09-28
Depends on how your connecting to the remote machine. Three common ways are Samba, sshfs, and NFS. Samba is used for windows machines. sshfs and NFS are mostly used for *nix* to *nix* networking.

a typical file on a networked server using Samba would look something like this
```
smb://<server name or ip>/<share name>/<folder name>/<file name>
```
example
```
smb://whitebox/stuff/down/foobar.txt
```

---

### Post by skullmunky on 2008-09-28
Correct, linux has no A: C: D: drives, etc.  Everything, including other drives, is all under /.

so instead of something like "D:\database\test.gdb", a linux path would be like "/home/me/database/test.gdb".  

/home might in fact be another physical drive, but this is transparent to the filesystem.  UNIX was designed from the ground up for systems with multiple drives, often networked, while windows still has the legacy of DOS to carry around with the whole drive letter thing.  

hope that was informative, though it doesn't answer your question :)

it sounds like your DB is on the same machine you're trying to access it from, which is good, that makes it easier.

try one of these
```

localhost: /home/fgn89/Documents/database/TEST.GDB
localhost: /home/fgn89/Documents/database/test.gdb
192.168.0.3: /home/fgn89/Documents/database/TEST.GDB

```

---

### Post by davidryder on 2008-09-29
Just a tip for future posts: it's much easier to read posts when commands and output are wrapped with CODE tags. 

Good luck!

---

### Post by fgn89 on 2008-09-29
Oh.. Sorry, I didn't know how to do that code wrap thing. ><

Haha, that helps a lot. Thanks y'all!

I'll give it a try. ^^

---

### Post by fgn89 on 2008-10-01
Mmhm..

Now that that works..

I am able to get it working, by self, to self.

But it won't work, if it's from, networked computer, to self.

I tried both, 

```
192.168.0.3:/home/fgn89/Documents/database/TEST.GDB

smb://192.168.0.3/database/TEST.GDB
```

But it just says, unknown database.

From what skullmunky said,

the equivalent to a filepath on windows,

```
192.168.0.3: D:\database\test.gdb
```

is

```
192.168.0.3:/home/fgn89/Documents/database/TEST.GDB
```

right?

---

