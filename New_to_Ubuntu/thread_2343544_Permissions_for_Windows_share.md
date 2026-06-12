---
title: "Permissions for Windows share"
date: 2016-11-17
forum: New to Ubuntu
---

### Post by stepan3 on 2016-11-17
Hello! I have the following task:
In our intranet we have Windows Share- "Share" Inside this Share i have 2 folders:'Important' and 'Trash'. I have a credentials to read and write in both folders. But i am not admin of this Share.
On my computer i have 2 users 'admin' (admin rights') and 'work' (Standard user rights). Under admin i permanently mount this share as network drive. And i have both read and write permissions for whole disk.

Problem:
Is it possible for work user make Read-Only permissions for folder Share/Important and Read and Write permission for folder Share/Trash.

Thank you in advance.

P.S. I have Ubuntu 16.04

---

### Post by oldrocker99 on 2016-11-17
The chmod (**ch**ange **mod**e) command will do the trick. Navigate to your share directory and enter this:
```
sudo chmod -R 444 Important
```
This will make the entire folder read-only for you, your group, and the user (including you).

For the Trash folder:```
 such chmod -R 777 Trash
```
This will make the folder read-write/execute for everybody. If you want that for only you:
```
sudo chmod -R 744 Share/Trash
```
That will give read-write-execute permissions for you, and read-only for everyone else.

---

### Post by oldrocker99 on 2016-11-17
The chmod (**ch**ange **mod**e) command will do the trick. Navigate to your share directory and enter this:
```
sudo chmod -R 444 Important
```
This will make the entire folder read-only for you the user, your group, and anyone else.

If you want read-write permissions for the user only:```
sudo chmod -R 744 Important
```

For the Trash folder:```
 such chmod -R 777 Trash
```
This will make the folder read-write/execute for everybody. If you want that for you only:
```
sudo chmod -R 744 Trash
```
That will give read-write-execute permissions for you, and read-only for everyone else.

7 means read-write-execute, and 4 means read-only. This is a good resource:[http://www.computerhope.com/unix/uchmod.htm](http://www.computerhope.com/unix/uchmod.htm)

---

### Post by stepan3 on 2016-11-19
Thank you. But the problem is that Share is really huge (50 Tb). And when i type this commands i wait 30 min and stop process. It seems it try to change permissions for each file...

---

### Post by kingneutron on 2016-11-30
--If you don't want to change the folder AND everything in it, don't use the -R (Recursive) option with chmod...  If you want to see what it did, add the -v option.

Example:
'/tmp # chmod -v a+r .X0-lock '
mode of &#8216;.X0-lock&#8217; retained as 0444 (r--r--r--)

--Since you manually stopped the process after 30 minutes, I hope you have a snapshot or a backup to revert to in case things got messed up.

---

