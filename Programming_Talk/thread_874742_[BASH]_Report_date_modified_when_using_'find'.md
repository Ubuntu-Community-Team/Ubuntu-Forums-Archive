---
title: "[BASH] Report date modified when using 'find'"
date: 2008-07-30
forum: Programming Talk
---

### Post by altonbr on 2008-07-30
I have a list of absolute directories I created using find and I need to know the date modified for each folder.

I tried replacing "\n" with " " and piping to 'ls -l' but that didn't work. 'ls -l', when I copied the result of ```
cat /list | tr "\n" " "
``` seemed to list the files in each directory and not the modification date of each folder, so I don't think 'ls' is the command I am looking for.

What else can I use? I noticed 'find' has "modified in the last _n_ days" but I need to know the exact date.

Thank you for your time!

---

### Post by ghostdog74 on 2008-07-30
you can use stat to find modification date
```

stat -c "%y" dir_to_check

```

---

### Post by altonbr on 2008-07-30
> **ghostdog74 said:**
> you can use stat to find modification date
```

stat -c "%y" dir_to_check

```

As always, thank you for your quick response!

Is there any way to pipe a directory list to stat? Such as 'find' or 'ls'?

Secondly, is there any way for it to print the directory name and then the modification date for each folder? Having a whole slew of modification dates with no folder name is difficult to read.

---

### Post by dwhitney67 on 2008-07-30
Extending ghostdog74's suggestion, try:
```
$ find . -type d -exec stat -c "%n - %y" {} \;
```

---

### Post by ghostdog74 on 2008-07-30
another way, without stat
```

find . -type d -printf "%t:%p\n"

```
check the man page of find to see what printf and it format specifiers mean.

---

