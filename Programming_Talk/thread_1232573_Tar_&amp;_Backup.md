---
title: "Tar &amp; Backup"
date: 2009-08-05
forum: Programming Talk
---

### Post by CatsRninja on 2009-08-05
hello everyone,


I`m trying to create an automatic backup script using the tar command.
Heres the algorythm(kinda) of what i have in mind.

1rst time:
1-backsup `tar -cf (name) (backupfolders)`
2-gzip name

2cond time backup:
1-search for previous backup,
if not there, run a 1rst time backup END
2- unzip previous backup;
3- tar -uf (name) (backupFolders)
4-zip backupfile


The point that bothers me, is the 2cond time 3rd tar, with the -u (update) saves a new copy of a file, example:
you have t.txt in the backup, you modify t.txt, so update updates the new t.txt, but doesnt delete the old one,
I dont want that to happen.
the new t.txt should override the last t.txt.

I hope i`ve been clear.

---

### Post by kieransimkin on 2009-08-05
I'd suggest checking this section of the tar documentation:
[http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html](http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html)

---

### Post by CatsRninja on 2009-08-05
Thanks kieransimkin, thats what i was looking for, incremental dumps.

---

### Post by lensman3 on 2009-08-06
Look at the program "star". It is a super-tar.  It does incremental backups by device/filesystem and will update a dumpdates file.

Here is my command line for backing up root:

star -c -xdev -sparse -acl -link-dirs level=0 -wtardumps f=$save_file -C / .

The dumpdates file is -wtardumps and is written in /etc.

---

### Post by CatsRninja on 2009-08-06
> **lensman3 said:**
> Look at the program "star". It is a super-tar.  It does incremental backups by device/filesystem and will update a dumpdates file.

Here is my command line for backing up root:

star -c -xdev -sparse -acl -link-dirs level=0 -wtardumps f=$save_file -C / .

The dumpdates file is -wtardumps and is written in /etc.


I got the tar script with incremental dumps working.
Thanks anyway.

---

