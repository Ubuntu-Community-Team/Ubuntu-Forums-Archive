---
title: "useradd not working or is it?"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Joe67 on 2013-04-07
ive tryed to add a user through putty

useradd ts3user
useradd: user 'ts3user' already exists

when i try go there 


root@:~# cd /home
root@:/home# cd ts3user
-bash: cd: ts3user: No such file or directory
root@:/home#

ive done this a few times now in the past and normaly works, it should save in /home

any ideas?

---

### Post by schragge on 2013-04-07
Perhaps *useradd* is not configured to create home directory for the user by default. You should have done either
```
useradd -m ts3user
``` or ```
adduser ts3user
```

---

### Post by Joe67 on 2013-04-07
ok thanks, since the user is already created is it possible locate and to move it?

---

### Post by steeldriver on 2013-04-07
you should be able to use *usermod *with the -d or --home option

---

