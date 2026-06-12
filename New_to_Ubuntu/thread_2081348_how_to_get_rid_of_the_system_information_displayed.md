---
title: "how to get rid of the system information displayed when."
date: 2012-11-06
forum: New to Ubuntu
---

### Post by hookitup on 2012-11-06
hello ppl,

so when i log into my server via ssh and normally on the computer itself as well i get the system information and stuff that displays
```
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

  System information as of Tue Nov  6 12:56:19 PST 2012

  System load:  0.13              Processes:           60
  Usage of /:   5.6% of 20.54GB   Users logged in:     0
  Memory usage: 10%               IP address for eth0: 192.168.1.21
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

95 packages can be updated.
43 updates are security updates.

Last login: Tue Nov  6 12:52:57 2012 from x.x.x.x

```how do i get rid of all this stuff??? is it something in the /etc/bash.bashrc or what ?

---

### Post by Lars Noodén on 2012-11-06
It is in /etc/motd, but that is generated automatically.  You should be able to remove some of the default contents:

[http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/server](http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/server) edition of Ubuntu but for the regular

---

### Post by Cheesemill on 2012-11-06
You can edit the /etc/pam.d/login and /etc/pam.d/ssh files and delete the lines that read:
```
session     optional     pam_motd.so
```

---

### Post by hookitup on 2012-11-06
[Cheesemill]("http://ubuntuforums.org/member.php?u=559258")

 that worked perfectly, although the ```
Last login: Tue Nov  6 14:50:09 2012 from X.X.X.X

```
 is still there , know how to remove that?

---

### Post by wojox on 2012-11-06
```
touch ~/.hushlogin
```

---

### Post by hookitup on 2012-11-06
thanks,

---

