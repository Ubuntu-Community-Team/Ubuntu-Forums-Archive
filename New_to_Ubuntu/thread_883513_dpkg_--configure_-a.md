---
title: "dpkg --configure -a"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by czman11 on 2008-08-08
I was updating language support and it got stuck. I tried to run it but I,m getting message to close synaptic since only one updater can run at the time.
I ran

sudo dpkg --configure -a

and I can see that the language support is still trying to run. I tried to stop it with Ctrl+C but nothing is happening. Can anyone give me an idea what to do?

Thanks

---

### Post by eightmillion on 2008-08-08
Try **sudo pkill -9 dpkg** first and then run **sudo dpkg --configure -a**

---

### Post by iaculallad on 2008-08-08
Use the kill terminal command to terminate the application. Or to view the apt processes running in background, try the command below:

```
ps aux | grep apt
```

Get the process ID listed of the running apt application and use kill to terminate it.

```
sudo kill -9 pid
```

---

### Post by juanc44 on 2008-08-08
Thanks guys, it also helped me.

---

