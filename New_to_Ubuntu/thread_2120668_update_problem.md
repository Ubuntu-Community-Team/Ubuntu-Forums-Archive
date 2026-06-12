---
title: "update problem"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by johnwill on 2013-02-27
Help needed please: Ubuntu 12.04 LTS Lenovo desktop dual boot windows 7;
In Terminal: sudo apt-get update && apt-get dist-upgrade  update continues ends with message: E: could not open lock file /var/lib/dpkg/lock -open(13:permission denied)
E:unable to lock the administration directory(var/lib/dpkg/),are you root?
I am still unable to use the numeric key pad are the two problems conected?
How do I continue.Thank you

---

### Post by praveensamineni on 2013-02-27
hi 
   

sudo apt -get update run this command

---

### Post by plucky on 2013-02-27
>  E: could not open lock file /var/lib/dpkg/lock -open(13ermission denied)
E:unable to lock the administration directory(var/lib/dpkg/),are you root?

That usually means that there is more than one package manager open and the other package manager has ownership of the lock file.
Close all other package managers before running ```
sudo apt-get update
```

also it could mean that a package manager didn't close properly and has kept the ownership of the lock file,in which case you will have to delete the lock file with ```
sudo rm /var/lib/dpkg/lock
``` and then run the update again.

Good Luck

---

### Post by schragge on 2013-02-27
This
```

sudo apt-get update && apt-get dist-upgrade

```
should be
```

sudo apt-get update && [color=red]sudo[/color] apt-get dist-upgrade

``` You forgot the second [color=red]sudo[/color]. The part that comes after && is **another** command, it needs its own sudo.

---

### Post by johnwill on 2013-03-01
Problem Solved: Thank you for the information,also solved the Numeric keypad problem.:P

---

### Post by plucky on 2013-03-01
Please mark your thread as **[Solved]** using "Thread Tools" at Top of the page

---

