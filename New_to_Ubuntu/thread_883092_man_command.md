---
title: "man command"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by catia2000 on 2008-08-07
Hi, How come the man command does not work under my Ubuntu server installation ??

---

### Post by maybeway36 on 2008-08-07
What is the error message you get?

---

### Post by catia2000 on 2008-08-07
I get 

bash: man: command not found

---

### Post by spiderbatdad on 2008-08-07
```
sudo apt-get install manpages man-db
```

---

### Post by catia2000 on 2008-08-07
Thanks !!

---

### Post by catia2000 on 2008-08-07
Strange ... I did the sudo apt-get install manpages
and it all looked correctly... took the files from the CD ...etc..

But I get the same error message when I try the "man" command ..?

---

### Post by glennric on 2008-08-07
Try installing the package "man-db"?  That is the package that actually contains the "man" executable.

---

### Post by gerben1 on 2008-08-07
perhaps this helps:
[http://ubuntuforums.org/showpost.php?p=5001881&postcount=15](http://ubuntuforums.org/showpost.php?p=5001881&postcount=15)

---

### Post by catia2000 on 2008-08-07
That did the trick : Try installing the package "man-db"

Thanks for all the sugestions ...!!!

---

