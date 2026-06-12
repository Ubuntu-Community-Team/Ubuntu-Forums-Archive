---
title: "how to find out disk space for all folders/dir? df --local?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by gotquestions on 2008-05-19
my home directory has lots of subdirectories. how can i know what is the disk space used for each directory? 
for example:

my pwd is: /home/lindsey/
and i have lots of subdirectories

/home/lindsey/music
/home/lindsey/pictures
/home/lindsey/essays

i typed df --local, it seems hard to understand

---

### Post by nirkir on 2008-05-19
try the following ```
du * -s
```

You can play with du parameters if you need different behavior

---

### Post by joshsmith on 2008-05-19
applications>accesories>disk usage analyzer

---

### Post by Ryadt on 2008-05-19
I would add 
du * -sh

---

