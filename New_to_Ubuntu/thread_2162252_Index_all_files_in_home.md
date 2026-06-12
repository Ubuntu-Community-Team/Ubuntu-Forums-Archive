---
title: "Index all files in home?"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by noersetiawan on 2013-07-13
How do I force Unity Dash to index all files on my home folder? Since the default can only find files I recently accessed (Zeitgeist, right?), which making search function somewhat useless for files.

---

### Post by ajgreeny on 2013-07-13
```
sudo updatedb
``` will update the file database which command **locate** uses.

Does that help?

---

### Post by noersetiawan on 2013-07-13
Is sudo updatedb index only my home folder? I don't want to run it if it will index whole /.

---

### Post by ajgreeny on 2013-07-14
No, it is the whole filesystem.

---

### Post by vanadium on 2013-07-14
You may be using an earlier version of Unity. Currently, Unity also uses locate to find files. In previous versions, only zeitgeist was used. If you are using an earlier version, then the tip of ajgreeny will not work.

---

### Post by steeldriver on 2013-07-14
fwiw you *can* tell updatedb to only index files starting from a given directory root e.g.

```
sudo updatedb -U $HOME
```

```

       -U, --database-root PATH
              Store only results of scanning the file system subtree rooted at PATH to the generated database.  The whole file system is scanned by default.


```

---

### Post by ajgreeny on 2013-07-15
Thanks for that, steeldriver.

I was not aware of that possibility of limiting the database, normally using pipe to grep to edit the output of locate, but that quick update of the database for a particular filesystem folder, eg /etc, could be very useful.

---

### Post by dannyboy79 on 2013-07-15
you can also use /etc/updatedb.conf to exclude certain paths, directory names, or even certain filesystem types

---

### Post by noersetiawan on 2013-07-16
I'm on 13.04.

sudo updatedb -U $HOME is a nice option, thanks!

---

