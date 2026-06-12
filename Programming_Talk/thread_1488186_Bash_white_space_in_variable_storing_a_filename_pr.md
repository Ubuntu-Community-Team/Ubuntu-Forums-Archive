---
title: "Bash white space in variable storing a filename problem"
date: 2010-05-19
forum: Programming Talk
---

### Post by terminator14 on 2010-05-19
Sorry I couldn't make the title any less confusing. Basically I was writing a script to automate some backups of files I have when I came across a bit of a problem. The simplified version of the problem is this:

I'm trying to understand why the following will not work as expected:

```
$ ls -l /home/user/space\ file 
-rw-r--r-- 1 user user 0 2010-05-19 17:05 /home/user/space file

$ TEST="/home/user/space file"; ls $TEST
ls: cannot access /home/user/space: No such file or directory
ls: cannot access file: No such file or directory

$ TEST="/home/user/space\ file"; ls $TEST
ls: cannot access /home/user/space\: No such file or directory
ls: cannot access file: No such file or directory

$ TEST='/home/user/space file'; ls $TEST
ls: cannot access /home/user/space: No such file or directory
ls: cannot access file: No such file or directory

$ TEST='/home/user/space\ file'; ls $TEST
ls: cannot access /home/user/space\: No such file or directory
ls: cannot access file: No such file or directory

```

If you haven't noticed the differences, it's every combination of (with/without escape character) and (single/double quotes). As far as I know, at least one of those should have worked (I would have figured either attempt 2 or 4). Any reason why they are not? This is bash version 4.1.5(1) by the way.

---

### Post by kaibob on 2010-05-19
The following will work:

> $ TEST="/home/kaibob/space file" ; ls "$TEST"
test file

---

### Post by terminator14 on 2010-05-19
Holy crap you're a genius! Thanks! Still looks kind of weird. How come that works? Why would $TEST be different than "$TEST"?

---

### Post by kaibob on 2010-05-19
> **terminator14 said:**
> Holy crap you're a genius! Thanks! Still looks kind of weird. How come that works? Why would $TEST be different than "$TEST"?

The Bash Reference Manual does a good job of explaining this issue:

[http://www.gnu.org/software/bash/manual/bashref.html#Quoting](http://www.gnu.org/software/bash/manual/bashref.html#Quoting)

This provides a somewhat less technical and perhaps more easily understood explanation:

[http://www.linuxtopia.org/online_books/bash_guide_for_beginners/sect_03_03.html](http://www.linuxtopia.org/online_books/bash_guide_for_beginners/sect_03_03.html)

---

### Post by terminator14 on 2010-05-19
Hmm... Now that I think about it, it sounds like it would interpret the variable as the string it represents while the "" would simply keep the two parts of the file name together - the "/home/kaibob/space" part and the "file" part. That sounds right?

I've been meaning to give the bash manual a read but never got around to it since I had school. Now that I'm done I'll give it a go. Thanks!

---

