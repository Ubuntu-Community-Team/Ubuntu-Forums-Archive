---
title: "Need help booting. PLEASE"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Lisa Y on 2008-07-04
Hello everyone,

PLEASE HELP, i have no idea whats going on with my laptop...all i saw was it was booting up.It went to the point where i saw the status bar loading then this is what i see...

```

Starting up...
Loading, please wait...

Ubuntu 7.10 root ttyl

root login:****
password: ***
Last login: Fri Jul 4 00:03:42 EDT 2008 on ttyl
Linux root 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 ITC 2008 i686

The programs included with the ubunt system are free software;the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

```

---

### Post by bwallum on 2008-07-04
Why not Hardy? It's nice and stable now.

---

### Post by Lisa Y on 2008-07-04
Can i upgrade to Hardy via only the command prompt...since i cant seem to boot in...?

---

### Post by bwallum on 2008-07-05
> **Lisa Y said:**
> Can i upgrade to Hardy via only the command prompt...since i cant seem to boot in...?

Do you have a live CD for 7.10? (or preferably 8.04)

---

### Post by bwallum on 2008-07-05
...also, if you are online and can get a terminal working in recovery mode (select from grub menu when you first boot up) try this:-```
apt-get dist-upgrade
``` If told you do not have permission then use this command instead:```
sudo apt-get dist-upgrade
```If you need to use sudo you will need to tell the system your password when prompted.

---

