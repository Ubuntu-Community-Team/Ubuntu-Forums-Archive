---
title: "cvs, how to commit new version"
date: 2008-02-07
forum: Programming Talk
---

### Post by Mr.Carramba on 2008-02-07
Hi!

I have several branches of the same project and have been commiting frequently so no file versions look nasty..
like 1.4.2.3.2.4.5.36.7.11.2 etc .. this is really ugly and I would like to be able to change file version to for ex. 2 or 3 ..
but I haven't managed to do it,

Hope you can help me!

Edit: command cvs commit -r 2.0
returns error "cvs commit: Up-to-date check failed for" for all files

---

### Post by anbumanij on 2008-02-07
Command is :


      cvs commit <filename>
      
After Commiting you should update it using 

       go the directory

      $var/www/html: cvs update <filename> or cvs update -d

---

### Post by Mr.Carramba on 2008-02-07
> **anbumanij said:**
> Command is :


      cvs commit <filename>
      
After Commiting you should update it using 

       go the directory

      $var/www/html: cvs update <filename> or cvs update -d

you don't have to specify file name to commit changes, if you are in working directory, it's enough  to use update and all files with changes will by commited

---

