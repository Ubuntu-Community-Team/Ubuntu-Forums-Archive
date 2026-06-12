---
title: "Are built in accounts secure (eg backup, bin, lp, etc)?"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by sheikjabooti on 2014-01-14
Hi all, this is my first post so hopefully i get lucky...
So I've been trying to get an Ubuntu server up and running for some time and am finally making some progress.  Webmin is certainly helping things along.

Anyway, I looked through the list of users and noticed there were heaps.  My biggest concern was security.  Are these users secure?  Do I need to change all their passwords.  What's stopping someone from logging in as those users?

Thanks for your help and sorry if its a dumb question.

---

### Post by Impavidus on 2014-01-14
The other users are all locked. Their passwords have been locked, so it's impossible to login as one of those users. You can use ```
sudo passwd -aS
```to see password information of all users. Whenever the second columns shows L the password has been locked. On  a default system, only the accounts of real (=human) users should have passwords, indicated by P. See ```
man passwd
``` for more information.

Techically speaking, it is possible to login to accounts with locked passwords using other methods, like ssh keys, but you'd have to set that up yourself. By default, passwords are the only way to login.

---

### Post by Dave_L on 2014-01-14
An alternative way to see that those users cannot log in is to look at /etc/shadow:

```
sudo cat /etc/shadow
```

The second field for each user is the encrypted password. If it's "*" or "!", that user cannot log in.

For more details:

```
man shadow
```

---

### Post by sheikjabooti on 2014-01-14
Thanks guys.  Really appreciate the help.

---

