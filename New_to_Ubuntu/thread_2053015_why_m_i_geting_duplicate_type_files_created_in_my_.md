---
title: "why m i geting duplicate type files created in my working dir"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-09-04
hi all
i m using ubuntu 12.04 LTS.... 
whenever i m creating a file in command line, e.g using touch i created a file aaa.txt,, afterwards when i list the files in working dir using ls,,, it is showing another file with the same name and ~ at the end,,, e.g for aaa.txt,, it creates aaa.txt~ aswell..this time the aaa.txt~ file generated is blank.... but tried  another abc.c file , the extra file generated abc.c~ is replica of original.... what is this ~... why this extra file is created??? whts use of it???why required???
plz explain a bit in detail,, as i m new to linux..........

---

### Post by Grenage on 2012-09-04
It's basically a temporary file, containing changes to documents that have not been applied.  You can disable autosave and such features from within gedit, which I assume is the offending application.

---

