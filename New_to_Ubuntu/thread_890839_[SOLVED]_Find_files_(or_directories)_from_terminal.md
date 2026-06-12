---
title: "[SOLVED] Find files (or directories) from terminal?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by BassKozz on 2008-08-15
What is the command to find files (or directories) from the terminal?

I've tried using the 'find' command, but that doesn't seem to drill down into subdirectories (or at least I am unfamiliar with the attribute required to do so).
TIA,
-BassKozz

---

### Post by drs305 on 2008-08-15
> **BassKozz said:**
> What is the command to find files (or directories) from the terminal?

I've tried using the 'find' command, but that doesn't seem to drill down into subdirectories (or at least I am unfamiliar with the attribute required to do so).
TIA,
-BassKozz

```

sudo find / -type f -iname *filename*

```

This will start at the root directory and search all folders/subfolders on the root partition. Since this will search /media and /mnt, if any partitions are mounted on these mount points they will be searched as well.

-type is either **f** for file or **d** for directory
-iname makes it case insensitive (e.g. *Box* or *box* will be found)

-maxdepth X will PREVENT the search from descending more than X levels

---

### Post by BassKozz on 2008-08-15
> **drs305 said:**
> ```

sudo find / -type f -iname *filename*

```

Thanks drs305,
BTW do you live in Miami (305)?


p.s. to anyone looking: [Find Man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?find") use '-type d' to find directories.
I read the Man page prior to posting this thread, but it was a bit confusing, so thanks again for helping decipher drs305 ;)

---

### Post by drs305 on 2008-08-15
> **BassKozz said:**
> Thanks drs305,
BTW do you live in Miami (305)?


p.s. to anyone looking: [Find Man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?find") use '-type d' to find directories.
I read the Man page prior to posting this thread, but it was a bit confusing, so thanks again for helping decipher drs305 ;)

Nope, east coast but not fla. ;-)

---

### Post by rampageoberon on 2008-08-15
I find the locate command very useful. The slocate database is automatically updated daily.

If you want to update the database then use the following command
```
sudo updatedb
```

To find the location of the file
```
locate <filename>
```

---

### Post by BassKozz on 2008-08-15
Thanks rampageoberon,

Can 'locate' find directories too?

---

### Post by tahina on 2008-08-15
You can also use tracker (the indexing- and searchtool with the orange magnifyingglass in the gnome panel) from the commandline, with the command tracker-search. (This is a bit overkill for finding files, though. It searches inside documents too.)

---

### Post by BassKozz on 2008-08-17
> **rampageoberon said:**
> I find the locate command very useful. The slocate database is automatically updated daily.

If you want to update the database then use the following command
```
sudo updatedb
```

To find the location of the file
```
locate <filename>
```
> **BassKozz said:**
> Thanks rampageoberon,

**Can 'locate' find directories too?**

:bump:

---

### Post by rampageoberon on 2008-08-18
Yes it does find directories as well as files.

---

