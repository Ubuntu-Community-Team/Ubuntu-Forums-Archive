---
title: "autorun program after x window (kubuntu) starts"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-06
Hi all, 

how do I set autorun program after x window (kubuntu) starts?

---

### Post by deadflowr on 2013-02-06
Go to System setting, then down to startup and shutdown, then set the program or script you'd like to autostart.

---

### Post by ajgreeny on 2013-02-06
If the application is still starting too quickly, ie, before your DE has started properly, use a compound command in the startup application command box, eg ```
bash -c "sleep 10; parcellite"
```which will delay parcellite start by 10 seconds, but use your own application command, not parcellite, of course.

---

