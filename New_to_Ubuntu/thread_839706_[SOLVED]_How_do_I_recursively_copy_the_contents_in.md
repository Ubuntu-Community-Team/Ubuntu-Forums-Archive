---
title: "[SOLVED] How do I recursively copy the contents inside of folder...."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Corrupt3d on 2008-06-24
From the terminal, I want to recursively copy files from inside a directory tree (ex: ~/home/), 
however _I only want to copy the files_ and **Not any of the folders** or any of the tree structure. 

I googled & looked through the man pages of ls and cp but couldn't find anything to do what I want.

---

### Post by sdennie on 2008-06-24
If you aren't concerned with the directory structure try:

```

cp -R ~/source_directory /path/to/destination

```

---

### Post by Inxsible on 2008-06-24
you can also use a combination of the find command and the exec flag. Have a look at the man pages for find to get an idea of how they are used.

I will try and conjure up something for you if i can...

---

### Post by Corrupt3d on 2008-06-24
> **vor said:**
> If you aren't concerned with the directory structure try:

```

cp -R ~/source_directory /path/to/destination

```

This copies the directory tree & all sub-folders.... :(
I only wanted the files

---

### Post by sdennie on 2008-06-24
Actually, looks like I wasn't thinking right and that cp -R keeps the directory structure.  Try:

```

find ~/source/ -type f -exec cp '{}' /path/to/destination \;

```

---

### Post by Inxsible on 2008-06-24
> **vor said:**
> Actually, looks like I wasn't thinking right and that cp -R keeps the directory structure.  Try:

```

find ~/source/ -type f -exec cp '{}' /path/to/destination \;

``` +1

vor seems to rbr commands more than I do ;)

---

