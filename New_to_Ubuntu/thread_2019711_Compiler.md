---
title: "Compiler"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by Manimallya on 2012-07-07
During compilation i am facing one issue..After the ./a.out is created whenever i am going to execute it its showing PERMISSION DENIED..Please resolve the issue..Thanks in advance..

---

### Post by nmaster on 2012-07-07
you should probably include more details... but try this:

sudo chmod u+x a.out

this will make the file executable for the user.  here are some basics on linux file permissions: 
[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

---

