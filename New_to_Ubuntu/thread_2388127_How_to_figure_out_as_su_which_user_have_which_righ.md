---
title: "How to figure out as su which user have which rights and run which tasks?"
date: 2018-03-28
forum: New to Ubuntu
---

### Post by dirk-lehmann on 2018-03-28
Which commands do I need to use to do that: How to figure out as su which user have which rights and run which tasks?

---

### Post by monkeybrain20122 on 2018-03-29
su is root. What is the reason for you to run as root? It is a security risk. You can  use sudo to run system level commands on a per command basis.

---

### Post by sudodus on 2018-03-29
Any user can run the following command (because the file /etc/group has read access for everybody)

```
grep '^sudo:' /etc/group
```

Look at the output! The user IDs after the last colon have sudo permissions (can run programs with elevated permissions via sudo).

---

### Post by Impavidus on 2018-03-29
sudo allows more fine grained control. /etc/sudoers and the files in /etc/sudoers.d/ specify which users can do what with sudo and whether they need a password. To read these files, you need root privileges. Most home users just keep these files at the defaults.

---

