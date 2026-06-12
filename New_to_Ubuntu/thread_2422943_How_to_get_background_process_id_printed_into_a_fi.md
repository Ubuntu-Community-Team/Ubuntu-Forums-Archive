---
title: "How to get background process id printed into a file ?"
date: 2019-07-15
forum: New to Ubuntu
---

### Post by anacondaonline on 2019-07-15
How to get process id printed into a file ?
I'm running a background process.
i'm trying to capture only pid into file.
But this does not log pid in file.
sudo nohup java -jar myapp.jar & >> mypid.log

---

### Post by Holger_Gehrke on 2019-07-15
$! in the shell gives you the PID of the last process placed in the background. So if you did
```

sudo nohup java -jar myapp.jar >> myapp.log 2>&1
echo $! > myapp.pid

```
you get the standard output and standard error output of the program in myapp.log and the pid in myapp.pid.

Holger

---

