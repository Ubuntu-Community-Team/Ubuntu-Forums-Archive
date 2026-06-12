---
title: "Locked out of account after trying to change user name"
date: 2016-03-26
forum: New to Ubuntu
---

### Post by joel44 on 2016-03-26
I wanted to change my user name so I created another admin account logged into it changed the permissions ran : usermod -l Newname oldname , changed the name of my home dir to newname. And now I can't get back it just reverts back to login screen so I logged into the other admin and found my normal account is stuck in root access

---

### Post by ashley-a on 2016-03-28
Hello joel44.

Can you login with a terminal (i.e. push ctrl+alt+f1 and login)?

---

### Post by retr02 on 2016-03-29
Because you changed the username etc ~ you will need to update the sudoers file with your new username.

I recall it being located in /etc/sudoers

---

