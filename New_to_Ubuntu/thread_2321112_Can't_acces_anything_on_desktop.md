---
title: "Can't acces anything on desktop"
date: 2016-04-20
forum: New to Ubuntu
---

### Post by Cozeh on 2016-04-20
Hi, i am new to linux and i've had this problem for some time and I think i know why it's happening but i don't know how to fix it.
I used this code by mistake: (or atleast something that looked like this)
```
chmod -x /home/username/Desktop
```

Thanks in advance

---

### Post by deadflowr on 2016-04-20
*Thread moved to **New to Ubuntu**.*

---

### Post by ajgreeny on 2016-04-20
All Directories must be executable or they will not work in the usual way.
See [http://askubuntu.com/questions/276690/why-does-chmod-644-make-directories-inaccessible/276858#276858](http://askubuntu.com/questions/276690/why-does-chmod-644-make-directories-inaccessible/276858#276858) for more details.

Why did you remove the executable permissions from it; did you find some suggestion somewhere that it might do something that you wanted?

Have a look at the output of command ```
ls -l
``` and I think you will find all the directories in home have permissions starting **drwx** but the final **------** may vary depending on your home security setting, normally **drwxr-xr-x** by default, but if you change them to 700 permissions it will be **drwx------**
I suspect your Desktop directory will now be showing **drw-r--r--** instead.

To solve your problem run command ```
chmod +x /home/username/Desktop
```

---

### Post by Cozeh on 2016-04-20
Thank you so much! It worked!

---

### Post by ajgreeny on 2016-04-20
Great!
Please mark as SOLVED from the Thread Tools menu up-top.

---

