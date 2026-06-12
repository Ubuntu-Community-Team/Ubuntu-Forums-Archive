---
title: "Bulk renaming tags"
date: 2008-12-04
forum: Programming Talk
---

### Post by b3n0 on 2008-12-04
Hey guys,
I'm looking to change the tag of some media files on my desktop.

They are in folders and sub folders like so.
*Nathan's Healing
>27Nov
5 .mod files and 3 .mpg files
>28Nov
8 .mod files and 5 .mpg files
>29Nov
8 .mod files

The .mod files work in Cinelerra providing the tag is renamed to .mpg. As I'm going to be constantly adding .mod files to the archive from my camera, I was wondering if there was a shortcut to bulk edit them. Maybe a command in terminal or a script.
Thanks for you help

---

### Post by b3n0 on 2008-12-21
Bump... any ideas?

---

### Post by unutbu on 2008-12-21
Do you wish to rename file extensions, or do you wish to edit tags inside the movie files? 

If it is the former, then this command will work:
```

find ~/Desktop -name '*.mod' -exec rename 's/.mod$/.mpg/' {} +
```

If it is the latter, then I don't know.

---

### Post by b3n0 on 2008-12-23
Thanks for your help, I'm trying to rename the file extensions. 
Eg movie.MOD needs to become movie.mpg
I tried what you suggested but it didn't work...
I also tried this...
```
 find /home/concorde/Desktop/Nathan's Healing -name '*.mod' -exec rename 's/.mod$/.mpg/' {} +
```
But that didn't work either...

Do I need to navigate to the folder first? 
/home/concorde/Desktop/Nathan's Healing
right now there are 7 sub folders inside that folder each containing some .mod's from my camera which need to be renamed. Is this coding going to to detect these sub folders?

Thanks again

---

### Post by slavik on 2008-12-23
do filenames end with mod or MOD? it could be a case issue.

---

### Post by b3n0 on 2008-12-23
> **slavik said:**
> do filenames end with mod or MOD? it could be a case issue.

.MOD caps

---

### Post by WW on 2008-12-23
> **slavik said:**
> do filenames end with mod or MOD? it could be a case issue.

...and a "spaces in the path name" issue.  It looks like the intended path is "/home/concorde/Desktop/Nathan's Healing", so quotes are required around the name.

---

### Post by b3n0 on 2008-12-23
Bingo! Thanks guys. Plus ones for all!
To make it easy I renamed the folder nh.

---

