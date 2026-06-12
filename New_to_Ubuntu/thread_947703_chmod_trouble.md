---
title: "chmod trouble"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by melrokz on 2008-10-14
The man pages of chmod do not give examples. Plz give examples and explain them. I've got one from the web: i compared it to the man pages, but it didn't make sense.
```
sudo chmod -R 777 /media/disk
```
Also plz explain all other uses of chmod.

---

### Post by bobnutfield on 2008-10-14
Sorry, delete post

---

### Post by o.besner on 2008-10-14
Wikipedia's article is pretty complete, you might want to read it.

[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

you can also have a look at the Linux Documentation Project

[http://tldp.org/](http://tldp.org/)

But you should know that if you right-click a file or a folder, select "properties", and then go in the "permission" tab, you can change the permission in a friendly, not-command-line way. Works for most of the files, at least in your home folder.

---

### Post by ethoxyethaan on 2008-10-14
when using Chmod you need to learn some simple binary,

owner [READ/WRITE/EXECUTE] group [READ/WRITE/EXECUTE] the rest [READ/WRITE/EXECUTE]

in short: 

rwxrwxrwx

##################################

you can assign a Digit to one of those values:

```
rwxrwxrwx
110110100
```

you split it up

110 110 100 

your first number would be: 6 (because 110 is 6 in decimal)
second: 6 
third: 4

this makes: chmod 664, and means:

Read/write for owners of the file, and users in the group of the file, and all the rest can only read the file.


Chmod is closely related to: chgrp and chown, best way to find info is to use a webcrabler! or the ubuntu/ linux help pages!

---

### Post by nothingspecial on 2008-10-14
This explains it pretty well

[http://www.codecoffee.com/tipsforlinux/articles/032-2.html](http://www.codecoffee.com/tipsforlinux/articles/032-2.html)

---

