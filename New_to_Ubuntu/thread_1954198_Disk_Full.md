---
title: "Disk Full?"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Old-un on 2012-04-07
I have a  200GB hard drive and for some reason when i tried to install software i am informed disk full? I am not a download junkie so what could be causing this? 

Could someone help me please

---

### Post by Basher101 on 2012-04-07
install Gparted (if not done so already), run it and post a screenshot

---

### Post by Dave_L on 2012-04-07
Or post the output from this command: ```
df -hT
```

---

### Post by pqwoerituytrueiwoq on 2012-04-07
check the contents of /var/log look for multi-gig files and delete one and install [bleachbit]("apt:bleachbit") and use it clean the rest
then keep a eye on log files and see hen its size grows drastically to figure out what is happening
in 9.04 i had a issue like that with a printer

---

### Post by ajgreeny on 2012-04-07
Is this a wubi install inside windows as that has a maximum size for the virtual disk of 30GB?

---

