---
title: "is there an equivalent to applescript for linux?"
date: 2008-01-16
forum: Programming Talk
---

### Post by demiurgen on 2008-01-16
this may not be the right place to post this. if so i apologies.

is there an equivalent to applescript for linux?
or a program that can automate repetitive tasks?

i have almost 3000 folders (ca 4Gb each) that i want to compress with rar (it more than halves them).

on a mac this is a breeze with applescript, but is there something similar for linux or maybe a program that can do stuff like this??

---

### Post by PaulFr on 2008-01-16
How are your 3000 folders organized ? I assume:

1. There is a single folder, and inside this folder, you have 3000 sub-folders each containing other files / folders,
2. You want to compress these sub-folders into 3000 rar archives, and
3. Your 3000 sub-folders were in **/home/dgen/movies** and there are no folders other than these 3000 in /home/dgen/movies.

I would open a terminal and run the command ```
cd /home/dgen/movies; find * -maxdepth 0 -type d -exec rar a {}.rar {} \;
```
The **find * -maxdepth 0 -type d** finds exactly the sub-folders of the current folder (and ignores any sub-folders of these folders).

For each such folder found, it executes the command **rar a <directory_name>.rar <directory_name>** where <directory_name> is expressed in the find command as **{}**.

If you want to remove the files and sub-folders of each of the 3000 folders as you create the corresponding rar archive, you can change the command to ```
cd /home/dgen/movies; find * -maxdepth 0 -type d -exec rar a -df {}.rar {} \;
```

This is just one way to do this - you could use scripting languages like Perl / Python to do this as well. Hope this helps.

---

### Post by mridkash on 2008-01-16
I don't know abt applescript but bash scripting is very powerful tool for performing repititive tasks.

Here is a site to get you started;

[http://tldp.org/LDP/abs/html/part1.html](http://tldp.org/LDP/abs/html/part1.html)

---

