---
title: "save the syslog before i change root password..."
date: 2008-04-22
forum: New to Ubuntu
---

### Post by lunaluna on 2008-04-22
hi , i want to recover my root password _but_ before that i want to save the system log files (if any) to check if someone logged in before me...
i am sure this is possible but how?

no problems with disks...(just to note)

---

### Post by Cypher on 2008-04-22
At the GRUB menu, login using the "Recovery Console" which will drop you to a shell, then go to the "/var/log" directory and take a look at the "auth.log" file. This file will contain information about who has logged in and what "sudo" commands were run.

Ubuntu doesn't use the "root" account and you are advised to keep it that way, use your account that you created during installation with admin privileges for all "root" work..

---

