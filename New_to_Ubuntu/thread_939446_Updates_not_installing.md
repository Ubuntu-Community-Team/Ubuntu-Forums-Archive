---
title: "Updates not installing"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by -jm- on 2008-10-05
I am running Ubuntu 7.04, and whenever I run the Update Manager, it indicates that I am up-to-date.  However, no updates have ever been installed since I installed Unbutu a month or so ago.  Do I have a problem?  -jm-

---

### Post by adobrakic on 2008-10-05
try 
```

sudo apt-get dist-upgrade
```

and i always like to do
```

sudo apt-get update --yes && sudo apt-get upgrade --yes 

```

---

### Post by -jm- on 2008-10-06
Code: thanks, but no luck - here's what happened... exactly nothing.  ny other ideas?
...~$ sudo apt-get dist-upgrade
...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by gandaran on 2008-10-06
system » administration » software sources » ubuntu software tab, tick the first four lines box, » update tab, tick the first two the security and recommended channels
next open synaptic package manager, click the reload/refresh button, now you can see all the updates available

---

### Post by -jm- on 2008-10-06
Gandaran - thanks - worked perfectly, and showed 238 updates available.  Perfect!  Best,  -jm-

---

