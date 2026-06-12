---
title: "MySql in file structure ?????"
date: 2008-10-10
forum: Programming Talk
---

### Post by hoboy on 2008-10-10
Maybe this is the wrong forum please forgive me.
Is it there a good ubuntu document to explain ubuntu file structure ? 
for example when I use synaptic to install a program where does that program is installed ? I can't find where MySql is installed in ubuntu file structure.
I mean a doc that explain in detail ubuntu file structure.
For example File System

---

### Post by geirha on 2008-10-10
Ubuntu follows the [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard). To see what files a specific package has installed, you can use ```
dpkg -L packagename
```

---

### Post by LaRoza on 2008-10-10
> **hoboy said:**
> Maybe this is the wrong forum please forgive me.
Is it there a good ubuntu document to explain ubuntu file structure ? 
for example when I use synaptic to install a program where does that program is installed ? I can't find where MySql is installed in ubuntu file structure.
I mean a doc that explain in detail ubuntu file structure.
For example File System

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

To find things, use:

```

whereis $PROGRAM

```

Or to find the program itself, use:

```

which $PROGRAM

```

```

~$whereis opera
opera: /usr/bin/opera /usr/lib/opera /usr/share/opera /usr/share/man/man1/opera.1.gz
~$which opera
/usr/bin/opera
~$

```

---

