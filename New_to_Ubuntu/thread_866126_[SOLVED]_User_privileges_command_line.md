---
title: "[SOLVED] User privileges command line?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by markprice on 2008-07-21
How do you set user privileges in command line? I added a user using adduser but how do I set his privileges now?

Thanks

---

### Post by Xerp on 2008-07-21
Best thing to do is to add the user to groups.

```
useradd -G groupname username
```

---

### Post by tamoneya on 2008-07-21
adding to groups should solve your problem.  I will be a little more specific.  Being members of different groups allows you to perform different tasks.  For example if you are a member of the admin group you can use sudo and administer the system.

---

### Post by markprice on 2008-07-21
Got it thanks!

---

