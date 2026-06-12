---
title: "Issues upgrading from 12.04 to 14.04.1"
date: 2014-10-20
forum: New to Ubuntu
---

### Post by mishi2 on 2014-10-20
Hello I am a fairly new Ubuntu user. I was trying to upgrade my system from 12.04.4 LTS to 14.04.1. I used the Update Manager to do this but something went wrong. After rebooting, the update manager just freezes. I tried to upgrade using the terminal and now I am getting errors. 


When I try sudo apt-get update I get this 


```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

The error persists even when I close all package managers / terminal windows / programs / restart. I have Synaptic installed but that is not open. I tried to find a solution to my issue in the forums but I'm not sure what is locking me from updating or how to find it. Any help is appreciated.

---

### Post by plucky on 2014-10-20
> E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Try deleting the lock file with ```
sudo rm /var/lib/dpkg/lock
``` and then run ```
sudo apt-get update
``` again.

Did the upgrade to 14.04.1 finish or did it restore 12.04.4?

Please post output from a terminal for ```
lsb_release -a
```

Good Luck

---

### Post by davit2 on 2014-10-20
Hi.
find apt process ID with following comand
$ ps aux | grep apt
and kill it
$ sudo kill -9 ****   (change **** with ID)

---

