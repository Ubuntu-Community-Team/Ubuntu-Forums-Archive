---
title: "Getting Systen Information in perl"
date: 2006-09-26
forum: Programming Talk
---

### Post by xaphan on 2006-09-26
I'm a bit new to perl and am trying to get some system information from it.  I need uptime and number of users logged in.  Anyone have any ideas?

Thank you in advance.

---

### Post by scxtt on 2006-09-26
do you have to use perl?

---

### Post by ghostdog74 on 2006-09-26
print `/usr/bin/uptime`;

---

### Post by xang on 2006-09-27
You could use the perl function system(). I believe this forks a subshell and returns you back to the calling program once the task is complete.

ex. 

system("who | wc -l");
system("/usr/bin/uptime");

You can do with the output as needed.

For not needing to return to the calling program, try using 
exec()

---

### Post by xaphan on 2006-09-27
Thanks xang! exec() worked like a champ!

---

### Post by xang on 2006-09-27
No problem! Glad that helped!

---

