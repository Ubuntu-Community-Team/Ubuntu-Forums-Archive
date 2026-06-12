---
title: "How to remove &quot;config.lock&quot;"
date: 2018-06-18
forum: New to Ubuntu
---

### Post by Odense on 2018-06-18
I am using "Lima Personal cloud" with a the Ubuntu Client ([https://install.meetlima.com/#linux](https://install.meetlima.com/#linux))

My Linux PC froze and I had to force a restart while running Lima.
Now I cannot start Lima - when I use the "start" command I get an error message - see below:


morten@morten-Lenovo-B50-10:/usr/bin$ lima start
Sat Jun 16 17:20:56 2018 default Lockpath /home/morten/.local/share/lima/config.lock is already locked, waiting for 60 seconds


How do I remove the config.log so I can use my Lima again?

---

### Post by Habitual on 2018-06-19
Hello:
In a terminal-emulator, I've been known to
```
rm /home/morten/.local/share/lima/config.lock
```

Verify lima is not started or running if the rm "barks" about being "in use"
and if it is not, then force it using
```
rm -vf /home/morten/.local/share/lima/config.lock
```in terminal

start lima.

---

### Post by Odense on 2018-06-20
Thanks a lot :-)
It worked - but not too happy delivering proof :-D

---

### Post by Habitual on 2018-06-20
Glad it worked out!

---

