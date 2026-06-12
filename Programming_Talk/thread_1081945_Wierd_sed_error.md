---
title: "Wierd sed error"
date: 2009-02-27
forum: Programming Talk
---

### Post by imyjimmy on 2009-02-27
Ok, so I'm getting this weird sed error while programming. I have a bunch of c code that have a variable named 'tofree' which I want to rename to 'freelist'

So of course, what I should do is:

sed 's\tofree\freelist\' getmem.c > getmem.c

and so on for every .c file.

You'd think this would work, but what happens is getmem.c is actually overwritten and turns into an empty file. WTF?

I had to svn revert everything. I thought sed was legit, what's going on?

---

### Post by Occasionally Correct on 2009-02-27
Writing to the file you're operating on via redirection can often cause data loss. You should either write to a temporary file (a > b; mv b a) or use sed's -i option. :)

---

### Post by geirha on 2009-02-27
This is because >file is interpreted by the shell, and not sed. When you type in that command, the shell will see that you want to redirect the output of a command to a file called getmem.c. So it truncates the file in preparation and starts the command ...

Look at sed's -i option. It does the change in-place, which seems to be what you want.

Also, \ is used to escape characters in sed's regular expressions. You should use / instead.

```
sed -i 's/\<tofree\>/freelist/g' getmem.c
```

---

### Post by imyjimmy on 2009-02-28
thanks you guys, the -i option worked.

---

