---
title: "getting zziplib to work in php5"
date: 2006-02-03
forum: Packaging and Compiling Programs
---

### Post by tamashii on 2006-02-03
I've been trying to get zip functionality working with php5, after installing php5, php5-cli and whatever those things depend on via Synaptic. From the description of php5-cli though, zip support is already suppose to be compiled with it. Yet i get errors like: 

Fatal error: Call to undefined function zip_open() in /path/file.php on line 79

still. I also installed zziplib-bin and libzzip-dev via Synaptic... any suggestions? Thanks.

---

### Post by prodigel on 2006-11-30
Hi. I'm having the same problem. Haven't digged too much yet but if you solved this issue please help me.

---

### Post by dark_religion on 2009-11-13
zip_open

  (PHP 4 >= 4.1.0, PHP 5 >= 5.2.0, PECL zip >= 1.0.0)
zip_open — Open a ZIP file archive
   


Did you install PECL zip?

---

