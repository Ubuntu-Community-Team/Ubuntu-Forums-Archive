---
title: "cant get in to root"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by silvama11 on 2012-02-12
I am the system admin  and sole user of this Ubuntu account.

I can login but I am not seen as the root user. Is there a command line code Ithat can fix this i already have one app that must be run from a root logged in user?

---

### Post by lisati on 2012-02-12
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by thomsebastin on 2012-02-12
> **silvama11 said:**
> I am the system admin  and sole user of this Ubuntu account.

I can login but I am not seen as the root user. Is there a command line code Ithat can fix this i already have one app that must be run from a root logged in user?
sudo su

---

### Post by benpack101 on 2012-02-12
Just because you are the only user on the machine, does not mean you will be signified as the root user. Running as the root user is dangerous and therefore if you want to run processes as root you must run sudo.

lisati's link is a good one to read more about it.

---

