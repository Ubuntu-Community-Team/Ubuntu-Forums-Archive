---
title: "[SOLVED] How to print a listing in a directory"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-09-24
I have saved several hundred .pdf files downloaded from various sources. I want to print the names of the files. I don't find a "print directory" feature in Ubuntu. 

I'ld prefer not to do a screenprint as I'll have multiple overlapping screens, an environmental waste.

I'm using Gnome for a desktop & file manager.

---

### Post by eentonig on 2008-09-24
There's probably a command to print from the cli, but I hardly ever print something, so I wouldn't know. But as a workaround, I can give you

> ls >> filetoprint.txt

This will put the output of the ls command in the file 'filetoprint.txt'. I guess you can figure out the rest...

---

### Post by silverglade00 on 2008-09-24
Open up terminal and type these in one at a time, pressing enter after each one:
```

cd Desktop
ls > files.txt

```

Then double-click the files.txt and print it.

---

