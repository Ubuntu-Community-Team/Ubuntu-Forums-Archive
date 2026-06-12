---
title: "difference in running fortran program via vmware and directly ubuntu"
date: 2012-10-06
forum: Programming Talk
---

### Post by chandukec on 2012-10-06
hi,
i wanted to run FORTRAN code in Ubuntu . I am able to run it successfully in ubuntu that is installed  via vmware by using make command and directly executing .exe file through it.
But the same thing when i tried in ubuntu(directly installed) does not work,in fact even after giving the .exe file by make file it is not running in the terminal.
Also if i tried to run it by "gfortran main.f" (directly installed Ubuntu) it is showing errors..
"undefined reference to ....." here .... are the corresponding calling functions/files.
Please help me out from this
Thank you

---

### Post by cariboo on 2012-10-08
A bump for the move.

---

### Post by conradin on 2012-10-08
try reinstalling gfortran

```
sudo apt-get install gfortran
```

---

