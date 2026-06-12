---
title: "script help ubuntu 20.04"
date: 2020-12-03
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-03
okay i am using this command to install a backup located in my home folder

tar xvpfj backup.tar.bz2 -C /

do i have to cd /home/ray/backups folder before i run the command or can i just run as is in terminal/tks

---

### Post by ActionParsnip on 2020-12-03
You should specify the full path to the backup file. The command may not be ran in the same folder as the archive. Using absolute locations means this isn't an issue

---

### Post by rburkartjo on 2020-12-03
act ?
so does it mean that i can just run the restore without cd first

---

### Post by rburkartjo on 2020-12-03
also is it necessary to switch to root to install the backup./tks

---

### Post by TheFu on 2020-12-03
> **rburkartjo said:**
> also is it necessary to switch to root to install the backup./tks

Look inside the tar - looks for owners, groups, permissions, ACLs, xattrs and whether the paths for every file and directory are relative or absolute.  Then decide which PWD is needed during restore.  I like relative paths to be used. That's much more flexible, but everyone has their own taste.

Tar really isn't a good system backup tool. It was created when 50MB was considered huge. Tar shines where we'd typically use a ZIP file, but want permissions too.  Something like moving source code or config files around between systems, assuming you don't just use rsync or store them into git instead.

backup.tar.bz2 has to be in the CWD/PWD to be found, so you'll either need to make that happen or provide the correct path to it.

---

### Post by rburkartjo on 2020-12-03
fu tks

---

