---
title: "[SOLVED] case sensitivity"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by venturosa on 2008-06-20
I have several hundred files stored on an external hard drive. The file system and the files have been created by 'Windows' and I receive additional files from other clients daily.  Since switching to Ubuntu I've found out that Linux file managers are case sensitive which is a slight problem for me as all these files start with the word 'Ref' or 'ref' or 'REF' followed by a number, and so Nautilus displays them in three sections rather than in the number order. Is there a way to get round this? I'm thinking possibly a command or a script that could change those first three letters of every file in a directory.

---

### Post by Flimm on 2008-06-20
Try pyrenamer or krename. You can install them from Applications, Add/Remove. I haven't tried them myself but they should do the job.

---

### Post by lazyart on 2008-06-20
Post #2 in this thread might help.  I would suggest running it in a copy of your data first...

[http://ubuntuforums.org/showthread.php?t=127491](http://ubuntuforums.org/showthread.php?t=127491)

---

### Post by Flimm on 2008-06-20
I got it using krename.
[list][*]On first run, choose tabbed GUI.
[*]In the tab Files, add the files you want to rename.
[*]In the tab Filename, type in the template field: rem[$4-]
[/list]
That will do exactly what you asked for, and keep the capitalization of the rest of the filename. Plus you get to preview the renamed filenames before clicking finish.

---

### Post by venturosa on 2008-06-20
pyrenamer works a treat. Does exactly what I wanted. Many thanks.

---

### Post by jakupl on 2008-06-20
You can also try thunar bulk rename
it can convert everything to lowercase or uppercase or whatever.

EDIT: too late.. oh well.

---

### Post by arsenic23 on 2008-06-20
Are they all in the same directory?  You could just use rename.

```
rename 's/[Rr][eE][fF]/ref/' *
```

---

### Post by jakupl on 2008-06-20
> **arsenic23 said:**
> Are they all in the same directory?  You could just use rename.

```
rename 's/[Rr][eE][fF]/ref/' *
```

Howcome rename has no recursive flag?

---

