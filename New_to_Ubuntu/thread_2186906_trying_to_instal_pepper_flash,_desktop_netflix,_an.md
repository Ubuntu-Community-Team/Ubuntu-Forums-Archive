---
title: "trying to instal pepper flash, desktop netflix, and pipelight"
date: 2013-11-09
forum: New to Ubuntu
---

### Post by mariodav9429 on 2013-11-09
every time i want to install something through the terminal i get a message like 

 Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mario@mario-Aspire-5536:~$ sudo apt-get install netflix-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mario@mario-Aspire-5536:~$ sudo apt-get install netflix-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?




and I dont seem to do anything ever on this terminal, what am I doing wrong?

---

### Post by bkline on 2013-11-09
You'll find some advice for dealing with that problem here: [http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem](http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem)

---

### Post by oldos2er on 2013-11-09
You can only have one package manager (or package manager front-end) open at a time. This includes Update Manager, Software Center, etc., so close those if they're open, then retry your terminal command.

---

### Post by mariodav9429 on 2013-11-09
I only have one open at a time

---

### Post by oldos2er on 2013-11-10
Then I'd try removing the lock file, updating and installing something. ```
sudo rm /var/cache/apt/archives/lock

sudo apt-get update && sudo apt-get install foo
```

---

