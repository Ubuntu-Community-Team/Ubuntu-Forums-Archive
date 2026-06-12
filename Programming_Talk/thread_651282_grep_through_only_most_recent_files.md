---
title: "grep through only most recent files"
date: 2007-12-27
forum: Programming Talk
---

### Post by sarnzzle on 2007-12-27
Hey this is probably a newbie question, but I'd appreciate the help.

I want to grep through only the most recent files. For example, I want to find all files that have a certain string, but only in files from the last 2 days. I'm pretty sure i've used it before, just can't remember it.

Anyone know the command?

Thanks for the help,
the sarnz

---

### Post by Martin Witte on 2007-12-27
something like  **find . -mtime -2 -exec grep -l '#!/usr/bin/env python' {} \;** put the string you're looking for between the quotes

---

### Post by sdrubolo on 2007-12-27
hi, I'm not completely sure but you should use the command find followed by the option -ctime -n. the explanation taken by the man page is :
 -ctime n
              File’s status was last changed n*24 hours ago.  See the
              comments
              for -atime to understand how rounding affects the 
              interpretation
              of file status change times.

for the minus is before n:

       -n     for less than n,
Hope this helps

---

