---
title: "how can I monitor the changes in a directory (for a local apt-repository)?"
date: 2005-06-05
forum: Programming Talk
---

### Post by josuealcalde on 2005-06-05
Anyone nows a way to monitor the changes in a directory (new files added or files removed). 

The idea is to execute a command when this occur.

I could pogram it checking for changes in an interval, but I would like to know if there is a way to put a process in backgraound which be able to wake up when changes in the directory occurs.
(I don't mind if it is a shell way or a langauje as C solution).

What I want is to monitor my local repository to update the control.gz when I donwlod a new .deb.


I also would like to know if there is a way of updating apt-database checking only one repository (for example, update only my local repository without updating all the repositories).

---

### Post by vague- on 2005-06-06
[http://www-128.ibm.com/developerworks/linux/library/l-inotify.html](http://www-128.ibm.com/developerworks/linux/library/l-inotify.html)

Hope that helps.

---

