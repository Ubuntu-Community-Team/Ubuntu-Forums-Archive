---
title: "adding date to backup folder"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-01-17
here is the my backup command
tar cvpjf backup.tar.bz2 --exclude=/proc4 --exclude=/mnt --exclude=/sys / --exclude=/lost+found --exclude=/tmp --exclude=/backup.tar.bz2

what do i need to add to the above so the finished tar.bz2 file will also show the date i backed up
tks

---

### Post by steeldriver on 2013-01-17
You could use the 'date' function inside a bash expansion - something like

```
tar cvpjf backup-$(date '+%F').tar.bz2 ... 
```The %F format specifier is YYYY-mm-dd i.e. it will give you

```
backup-2013-01-17.tar.bz2
```If you want a specific date format you can see all the possible specifiers by doing

```
man date
```and then cook something up from there

---

### Post by rburkartjo on 2013-01-17
steel tks will give that a try

---

