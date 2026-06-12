---
title: "copy paste multiple command in single line"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by termvrl on 2012-10-17
hi all.

i wondering if there any way to copy paste multiple command into single line.

for eg:
command 1: go to dir.. cd /usr/lib...
command 2:make a new folder in the dir.. mkdir 20121016
command 3:copy into new folder.. cp * 20121016

im using putty to remote my machine, so everytime to backup my folder, i doing this. copy paste one by one command. 
how i can put all three command in single line, so that i just need to copy paste one time only.

Thanks.

---

### Post by NikTh on 2012-10-17
Hi , 

you can do it with && or ; symbols 

example 

```
cd /usr/lib;mkdir 20121016;cp * 20121016
```
OR
```
cd /usr/lib && mkdir 20121016 && cp * 20121016
``` 

Thanks

---

### Post by termvrl on 2012-10-17
Thanks =D

---

