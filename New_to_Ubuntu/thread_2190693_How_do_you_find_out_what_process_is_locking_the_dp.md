---
title: "How do you find out what process is locking the dpkg database?"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by frogwarrior on 2013-11-28
When I'm installing an application and it gets stuck during the installation process, I usually kill the terminal then I can't use apt-get or dpkg until I reboot because there is still a process using /var/lib/dpkg. How do I find out what process is using it, so I can kill it? Just there, I was installing oracle-java8-installer and it froze. I ran top, and saw that there was a process using wget, so I knew that was the java8 installer, I killed that then the lock was removed. That was pure luck that I found the process like that, how can you find out what process is using dpkg?

---

### Post by Bashing-om on 2013-11-28
frogwarrior; Hi !

For starters do :
```

sudo lsof /var/lib/dpkg/lock
##or maybe:
sudo fuser -vki /var/lib/dpkg/lock

```
Then with the PID known, you can kill the process.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

