---
title: "Could not get lock /var/lib/dpkg/lock"
date: 2017-02-07
forum: New to Ubuntu
---

### Post by anju-t on 2017-02-07
Hi,

I checked with the older forum "[COLOR=#000000][SOLVED] Problem with update- Unable to lock Administration directory".

According to that The output I am getting is ,

[/COLOR]lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.

I am trying to install pip using the command,
apt-get install python-pip

The output is,
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Can someone help me to solve this.




Thanks

---

### Post by deadflowr on 2017-02-07
use sudo
```
sudo apt-get update
sudo apt-get install python-pip
```

---

### Post by anju-t on 2017-02-07
Thanks a lot it solved my problem.

---

### Post by deadflowr on 2017-02-08
Cool.
Here's some more about sudo:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you feel the problem has been solved [please mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

