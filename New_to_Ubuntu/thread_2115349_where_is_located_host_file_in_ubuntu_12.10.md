---
title: "where is located host file in ubuntu 12.10"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by MrBledi on 2013-02-12
hello all... i'm having a great experience with ubuntu 12.10 but i was wondering, where is located host file??
i know that could sound like a dump question, cos it will be the same even with the other ubuntu versions.... 

Greetings!

---

### Post by tgalati4 on 2013-02-12
Open a terminal:

```
cat /etc/hosts
sudo nano -B /etc/hosts
```

The second command is to edit the file.  Control-O to write (Output) the file.  Control-X to eXit.  Backup file will be called ~hosts.  Location of the hosts file has not changed in 30 years of using Unix and Linux.

---

