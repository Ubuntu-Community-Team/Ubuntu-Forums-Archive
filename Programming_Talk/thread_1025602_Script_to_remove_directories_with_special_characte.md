---
title: "Script to remove directories with special characters"
date: 2008-12-30
forum: Programming Talk
---

### Post by cjnkns on 2008-12-30
Hello all - 

As the title mentions I am looking for a script that will remove special characters in folders or files.

Anyone know where i could find this?

Thanks!

---

### Post by ghostdog74 on 2008-12-30
if you want a ready script, you can check out my Python script in my signature called filerenamer. Depending on what special characters you have, here's an eg usage
```

# ls -1
002.jpg
01.jpg
5346.jpg
file_with_3$^_special.txt
sfs.txt
test.jpg
test032.jpg

# filerenamer.py -p "[^a-zA-Z0-9]" -e "" -l "file*.txt"
==>>>>  [ /home/images/file_with_3$^_special.txt ]==>[ /home/images/filewith3specialtxt ]


```
remove "-l" to rename files.

---

### Post by cjnkns on 2008-12-30
Pardon my limited knowledge of python, but will this work on directories?

---

### Post by kaibob on 2008-12-30
I'm not sure what you're looking for but you may want to look at the following thread:

[http://ubuntuforums.org/showthread.php?t=1019412](http://ubuntuforums.org/showthread.php?t=1019412)

The rename command works on both files and folders.

---

### Post by cjnkns on 2008-12-30
I think that was what I needed - thanks for the link :)

---

### Post by kaibob on 2008-12-30
The precise command is:

```
rename -n 's/[;?|\\]//g' *
```

This will remove the characters ; and ? and | and \ from all files and directories in the current directory. You can, of course, change these characters to whatever you like. Also, you can change * to a file name or whatever you like. 

I've tried this command with various characters and they all work fine, except the back-slash, which has to be escaped, and the single quotation mark, which doesn't work even if escaped.

---

