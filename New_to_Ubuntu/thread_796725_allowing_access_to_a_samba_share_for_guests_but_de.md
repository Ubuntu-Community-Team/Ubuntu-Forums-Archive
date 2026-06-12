---
title: "allowing access to a samba share for guests but denying access from local users."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by fhqwhgad on 2008-05-16
I've setup my samba to be a fileserver for the windows machines on my network. Just a network drive basicly.
The folder needs to be writeable by guest users, however, if i could deny access from local users on the server, that would be sweet.
I don't want users ssh'ing into the machine to have access to the folder /home/fileserver/, but everyone accessing the folder through Samba should have write access.

Is this possible somehow?

---

### Post by PinkFloyd102489 on 2008-05-16
Remove the users from the sambashare group. In a terminal, do this:

```
nano /etc/group
```

Scroll all the way down (it's the last group) and check which users are listed beside sambashare. Remove uneccessary users.

Ctrl+o to save, ctrl+x to exit nano.

---

### Post by fhqwhgad on 2008-05-16
> **PinkFloyd102489 said:**
> Remove the users from the sambashare group. In a terminal, do this:

```
nano /etc/group
```

Scroll all the way down (it's the last group) and check which users are listed beside sambashare. Remove uneccessary users.

Ctrl+o to save, ctrl+x to exit nano.
So the people accessing the share over the network (windows machines), do they authorize as group?
I have set it to guest ok = yes.

---

