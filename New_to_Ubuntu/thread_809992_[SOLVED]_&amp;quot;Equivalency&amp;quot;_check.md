---
title: "[SOLVED] &amp;quot;Equivalency&amp;quot; check"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Victormd on 2008-05-27
Ok, so I have ~100Gb of mp3 all sorted in several directories together with album art and some ini files (created by windows). In windows, if I wanted to list or delete the ini files, I could simply
```
dir /s *.ini
```
or
```
del /s *.ini
```
and that would list or delete all *.ini files. 
How do I do that in Ubuntu?
I typed ls --help but couldn't find equivalent commands. furthermore, I couldn't use * as a "wild-card" and I'm not really willing to experiment with "rm"... :)
Any suggestions? At least for the list command. I know that I can type ```
rm -- '.ini'
``` or something like that to remove all *.ini files but would like to know the list command as well...

---

### Post by gsmanners on 2008-05-27
dir /s *.ini -> find . -name '*.ini'
del /s *.ini -> rm `find . -name '*.ini'`

(note the backwards apostrophes in the second line)

---

### Post by Sarah L on 2008-05-27
The list command in UNIX is fun and easy to use :)

For starters, you can use ```
ls
``` to show all the files in a directory.

If you want to view them in a list that shows more detailed info, use ```
ls -l
```

If you only want to view your *.ini files, try ```
ls -l *.ini
```

Now, RM is a more dangerous, but equally fun tool! If you're just playing around with it, use ```
rm -vi
``` so you can see exactly what's going on and be prompted before each change. If you're hellbent on removing something from your system, use ```
rm -rf
``` which will force a recursive deletion. Use caution when using this command!

---

### Post by Victormd on 2008-05-27
> **Sarah L said:**
> The list command in UNIX is fun and easy to use :)

For starters, you can use ```
ls
``` to show all the files in a directory.

If you want to view them in a list that shows more detailed info, use ```
ls -l
```

I'm not trying to see the files in one directory, I'm trying to list the files in the entire directory tree (5+ subdirectories in the structure)... :)
```
ls or ls-l
``` will only list the files in a single directory...

---

### Post by Victormd on 2008-05-27
> **gsmanners said:**
> dir /s *.ini -> find . -name '*.ini'
del /s *.ini -> rm `find . -name '*.ini'`

(note the backwards apostrophes in the second line)

The ***find . -name '*.ini'*** works fine but the ***rm `find . -name '*.ini'`*** will not remove the files from a directory with a composite name (i.e., "/Deep Purple")

I wonder if there is a more direct way of doing this...
UPDATE:
Using this command did the trick!
```
find . -name '*.ini' -delete
```

---

