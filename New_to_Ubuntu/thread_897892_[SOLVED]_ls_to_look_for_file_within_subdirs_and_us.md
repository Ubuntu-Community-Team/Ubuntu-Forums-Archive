---
title: "[SOLVED] ls to look for file within subdirs and using wildcards"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by ubguess on 2008-08-22
what is the syntax to look for a file on a hard drive (from the root) throughout all the subdirectories using wildcards?

For example in windows the command would be c:\dir *.inf /s

Thanks.

---

### Post by jerome1232 on 2008-08-22
lets say you wanted to find all mp3s
I use sudo because as a normal user you don't have read access to the whole system.
```
cd /
sudo find -name "*.mp3"
```
for more info check out the man page
```
man find
```

as an afternote, that command might bring so much input you can't scroll through it all, in that case pipe it to less

```
sudo find -name "*.mp3" | less
```

---

### Post by bobnutfield on 2008-08-22
I think you are looking for the "find" command.  Just type:

> man find

to get all the syntax and options

---

### Post by Majorix on 2008-08-22
```
sudo updatedb
locate *whatever_with_wildcards_supported*
```

I use this, because if you frequently update your db (with the first command) you will get much faster results compared to find or whatever.

For GUI there should be Search under Places. Not sure if it works properly though, used to fail on me.

---

### Post by jerome1232 on 2008-08-22
Nice tip, I didn't know about locate, and apparently it's updated every day by cron, it is noticeably faster too.

---

