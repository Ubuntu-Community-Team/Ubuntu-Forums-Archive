---
title: "[SOLVED] bash bug?"
date: 2007-10-22
forum: Programming Talk
---

### Post by Westerberg on 2007-10-22
From the bash man pages:

> Composite patterns may be formed using one or more of the following sub-patterns:
. . .
!(pattern-list)
       Matches anything except one of the given patterns
In other words, you can include all patterns *except* the few you want to exclude.
E.g., in a directory containing a mix of .html, .pdf, .avi, and .txt files, you should be able to delete all files except *html by entering:

```

james@james-desktop:~/Documents$ rm !(*html)
bash: !: event not found


```Anyone know what's going on?

---

### Post by digitalbenji on 2007-10-22
I just tested this by creating a folder and touching several randomly ending files in it, and only one with a .html extension.  It worked perfectly for me.  
>  bash --version
GNU bash, version 3.2.13(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.


Maybe you have an older version or something?  I did this on a 7.04 box as well.  I would be careful about using rm with pattern matching, but thats just me, and I don't like deleting things accidentally (not saying you do).

---

### Post by duff on 2007-10-22
```
# shopt -s extglob
```

---

### Post by Westerberg on 2007-10-22
That worked.  Thanks.

---

### Post by digitalbenji on 2007-10-23
could you give an explanation of that code please?

---

### Post by duff on 2007-10-23
shopt -- shell options
-s -- set variable
extglob -- extended glob rules

run "shopt" to see all variables. Use -s to set a variable, -u to unset, and the bash man page to an explianation.

---

### Post by digitalbenji on 2007-10-24
Neat, thanks.

---

