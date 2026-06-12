---
title: "How to know if my script is sleeping"
date: 2013-10-26
forum: Programming Talk
---

### Post by akshay-sulakhe on 2013-10-26
Hey guys, I want to run a script, but i should know if the script is sleeping. Like for eg: it should print 1 when it is sleeping. rest of the time i want it to calculate value of pi... Just for fun this is, nothing else. Any ideas?

---

### Post by ofnuts on 2013-10-27
Have it write a file into /var/tmp just before going to sleep, and erase the file on wake up?

Otherwise, if you have the PID, "cat /proc/$pid/stat" or "cat /proc/$pid/status" ("stat" is for programs, "status" is for humans) and check the "state": see [http://linux.die.net/man/5/proc](http://linux.die.net/man/5/proc)

---

