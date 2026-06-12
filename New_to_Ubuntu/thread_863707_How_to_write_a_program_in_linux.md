---
title: "How to write a program in linux"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by just_linux on 2008-07-18
Hi Every one,
I am very new to linux and I am just learning basics.:popcorn:
Just for start I want to learn how to write a code.
If you might know In DOC we could change all files which starts with a to b.
So it the file was ahjg.txt it became bhjg.txt with only one commend ren a*.* b*.*
Or if we wanted to change all txt file to doc we just type ren *.txt *.doc

So Now I want to write a code that does the same thing "It might be there already but I want to learn how to do it"

So please let me know "And if you are very kind, please write it out "
So I could put rename *.txt *.doc and just work and echo the number of files and path of each one.

Thanks A LOT :guitar:

Oh alos I do not know what ```
export LC_ALL='C'
```
and what ```
tr -cs 'A-Za-z' '[\n*]' | sort -u | comm -23 - words
```
means 
Please explain complity. 
Thanks :KS

---

### Post by schauerlich on 2008-07-18
You might get better help in the Programming Talk section of the forums:
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Be sure to check out the sticky first, as it holds a lot of good information that could possibly answer your question before you post it.
[http://ubuntuforums.org/showthread.php?t=832449](http://ubuntuforums.org/showthread.php?t=832449)

---

### Post by issih on 2008-07-18
The rename command should help you out rather a lot :)

[http://linux.die.net/man/1/rename](http://linux.die.net/man/1/rename)

As for the other bits you asked about, the export command is basically used to set an environment variable. In this case a variable named LC_ALL is being set to 'C'.

The other command is quite complex, its a translation command the results of which are piped into a sort comand and then thats followed by a comparisson command, some context is really necessary to work out what it might be trying to achieve.

---

