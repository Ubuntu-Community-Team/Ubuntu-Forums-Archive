---
title: "trim left so the string only show the right info"
date: 2019-07-25
forum: Programming Talk
---

### Post by cazz on 2019-07-25
hi
I have a variable that have a loong address to some folders.

Example 

**/var/www/html/site/directory/lib/folder_1**

I like to remove **/var/www/html/site/directory/** so I only **get lib/folder_1**


I have search but not find anything easy to understand.
Some say I can use regex but I have problem to understand how it works (is that any good online generator for that?)

---

### Post by TheFu on 2019-07-25
I would use cdpath.  It is a built-in variable for bash.
You could use symbolic links too.
Or you could use more wildcards to get there. If there is only 1 directory, then use /*/ where possible.
cd /v*/w*/h*/s*/dir*/lib/f*

Lots of choices.

[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)

---

### Post by norobro on 2019-07-25
As TheFu says, "lots of choices":```
$ var="/var/www/html/site/directory/lib/folder_1"
$ echo "${var#*/*/*/*/*/*/}"
lib/folder_1
$ echo $var | cut -d'/' -f7-
lib/folder_1

```

---

### Post by cazz on 2019-07-25
Wow it was fantastic, did never know I can do that. Thanks alot it works for me :)

---

### Post by TheFu on 2019-07-25
You can pattern match on any part of the path/file name. The pattern used just needs to be unique.
cd  /*r/w*/*l/*/*y/*i*/*1

But for long paths, I use symbolic links from my HOME or cdpath.  cdpath is powerful, but it is best used for unusual directories, not directories like "lib".  Play with it and you'll quickly learn why.

I think this stuff is covered in beginning Linux courses ... and books. It is in my classes, but I don't know about others.

---

