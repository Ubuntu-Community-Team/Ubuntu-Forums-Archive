---
title: "FTP permissions problem"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by cbwestrunner on 2008-07-05
Hello all,
I have been using gproftpd (proftpd with that graphical interface- I don't want to dabble in a non-gui thing just yet lol)for FTP transfers for my friends and I. Trouble is, when someone besides me uploads something, it can't be deleted no matter what I do. How can I reset the permissions on files and folders so that I can delete them off the HD? That's all, Cheers!

---

### Post by reeseslover531 on 2008-07-05
you can right click on the files in your HD and go to permissions, or from the command line you can chmod 777 (file name).  This will give all access to everyone on the file.  you might have to do the chmod as sudo though.

---

