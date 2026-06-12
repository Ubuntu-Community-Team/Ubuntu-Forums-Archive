---
title: "[SOLVED] when is sbackup finished?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by tstack77 on 2008-06-04
I forgot to write down the process id. Is there any other to find out if sbackup is still running beyond running the ps aux command?

---

### Post by Paqman on 2008-06-04
Look in system monitor. It shows all the processes currently running.

---

### Post by kpkeerthi on 2008-06-04
```
ps aux | grep -i <process-name>
```
E.g. ```
ps aux | grep -i nautilus
```

---

