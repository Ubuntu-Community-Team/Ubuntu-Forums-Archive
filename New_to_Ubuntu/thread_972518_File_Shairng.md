---
title: "File Shairng"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by onlyproductions on 2008-11-05
I setup my linux computer as a kind of home server i want to be able to create or delete files on it form any where

When ever i try to share my home folder it says i do not have the appropriate permissions 
how do i gain these said permissions

---

### Post by brandoncolorado on 2008-11-05
[http://ubuntuforums.org/showthread.php?t=445213](http://ubuntuforums.org/showthread.php?t=445213)

 I can tell you what I do.  Check out dropbox, it creates a file on your computer that you can access on their website, and that folder can exist on multiple computers
[https://www.getdropbox.com/](https://www.getdropbox.com/)

---

### Post by flameproof on 2008-11-05
I presume you have Samba installed and can see the directory from other PCs.

In Ubuntu click the directory > permissions > set all to read and write.

If you have the message "you are not the owner"  do this:

press ALT+F2 

type

gksudo nautilus

And do the same again.

---

