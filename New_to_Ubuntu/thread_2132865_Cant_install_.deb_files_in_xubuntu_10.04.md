---
title: "Cant install .deb files in xubuntu 10.04"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by meathdeath on 2013-04-06
Dear forums,

Before you get all mad and go "10.04 is old" and rage quit on me just ask yourself- WHAT WOULD JESUS DO? no im just kidding but seriously, hear me out- I am using a certain distro that the admins would not approve of that is based off of this and thats the reason im using it.  Now that we have established this i think it would be a good time to dive right into the problem.  My problem is that when i try to install a .deb file on Xubuntu (or gnome for that matter) it always gives me the same exact error which reads "Only one softare management tool is allowed to run at the same time" (please close the other application... and i have no idea what other application it is referring to as I am not currently attempting to install anything else simultaneously.  Any help/ideas would be much appreciated...

meathdeath - out

---

### Post by Cheesemill on 2013-04-06
If you're ***sure*** that you don't have anything running that uses apt (Software Centre, Update manager, apt-get command etc) then you can delete the lock file...
```
sudo rm /var/lib/dpkg/lock
```

10.04 hasn't reached end-of-life quite yet, you have until the 9th of May before the repositories get taken off line.

---

### Post by meathdeath on 2013-04-06
Thanks you for your response,

it seems to not have worked though:(

meathdeath

---

