---
title: "Access permissions problem"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by niknikme55 on 2013-03-08
HOw to solve the access permission problem for any folders in ubuntu??I am currently trying to copy a folder from one ubuntu to another ubuntu machine using "scp" command.scp -r foldername ipaddress_of_other_machine:directorypathIt shows like this:[http://ubuntuforums.org/images/smilies/confused.gifscp:](http://ubuntuforums.org/images/smilies/confused.gifscp:) permission denied.Please help....

---

### Post by vanadium on 2013-03-08
The problem looks like you do not have the necessary permissions on the receiving machine. Make sure that you write to directories that you own and that have write permissions for you on the remote machine as the user with which you log in there.

---

### Post by Sef on 2013-03-08
Moved to ABT.

---

