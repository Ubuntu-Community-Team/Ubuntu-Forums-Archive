---
title: "cannot find all files under /host"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by AmazinglySmooth on 2008-10-12
I just installed Ubuntu through Wubi last night, but I cannot find all of my files under /host.  I'm trying to get MT-Daapd to run, but I can't point it to my MP3's since they are under /host/Documents and Settings/.  I can browse to "Documents and Settings", but no files exist.

I read about locale issues, but I'm only using English.  The host PC installed Ubuntu from Vista Home Premium.  The machine is an Intel Quad Core.

Any ideas?

---

### Post by pytheas22 on 2008-10-12
Do files exist elsewhere under /host (e.g. under /host/Program Files, or whatever the Vista equivalent of Program Files is)?  Also, go to View>Show Hidden Files to make sure that hidden files are being shown.  This shouldn't be necessary but can't hurt.

If none of the above helps, what is the output of:
```

ls -al /host/Documents\ and\ Settings
```

---

### Post by AmazinglySmooth on 2008-10-12
$ ls -al /host/Documents\ and\ Settings
total 24
drwxrwxrwx 1 root root     0 2006-11-02 07:02 .
drwxrwxrwx 1 root root 24576 2008-10-11 01:08 ..

Some files do exist elsewhere, but I haven't checked if those listings show all of the files.

---

### Post by pytheas22 on 2008-10-12
That's strange...it seems to think that something is there ("total 24") but it doesn't list anything.  I'm not sure what the problem could be other than a weird wubi issue.

If you still don't have any luck figuring this out and no one else responds, please let me know and I'll see if I can think of anything else to check.

---

