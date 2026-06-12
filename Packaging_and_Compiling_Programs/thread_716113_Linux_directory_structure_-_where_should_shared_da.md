---
title: "Linux directory structure - where should shared data files be located?"
date: 2008-03-05
forum: Packaging and Compiling Programs
---

### Post by VictorR on 2008-03-05
I am thinking of developing a software, which should deal with tables (databases). Tables and their indexes must have read-write permissions.
Where should  these tables reside to be accessible:
1. by different users, logged to the same computer (not simultaneously).
2. by users, logged simultaneously on different computers in the LAN

For the case 1 is it possible, that the program could create a new set of tables, which would be accessible for other users, without asking for root privileges?

Thanks in advance.

---

### Post by justleen on 2008-03-05
the database would handle permissions in that case. You'd add user to the users-field in the database, and grant permission to those user on the database they actually need to go into.

if the tables you describe are seperate files on your system, you could use any dir, really. a logical place would be in /usr/share, or maybe /opt (tional) 

you can create a new group, and add users:
```

$ sudo addgroup table_users
$ sudo usermod -G table_users <username>

```

change the owner ship of the shared folder so user can read/write to it
```

$ sudo chgrp /opt/shared_folder table_users
$sudo chmod g+rw /opt/shared_folder 

```

---

### Post by VictorR on 2008-03-09
Thank you, Justleen,

As there are no other responses, I may assume that people mostly agree wit you :)

Because /usr/share is a read-only folder for users, the tables should be located in
/var/opt/<program-name>
and there must be 
/opt/<program-name> as well with the program itself.

Source:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

