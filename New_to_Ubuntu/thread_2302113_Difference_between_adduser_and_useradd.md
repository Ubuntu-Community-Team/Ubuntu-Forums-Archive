---
title: "Difference between adduser and useradd?"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by moebob24 on 2015-11-07
I've seen both of these, what is the advantage to using one over the other?


Seems as though they do the exact same thing.

---

### Post by sandyd on 2015-11-07
adduser is a perl wrapper for useradd, which is a low level tool for managing users

You'll probably notice that if you use useradd, users are not created with anything you would expect from a standard user. Instead, the user is created with the bare minimum (just the creation of the user ID), no home folder/etc.

If you use adduser, you will notice that it asks you questions, asks you for a password/etc. These options are passed onto useradd.

---

### Post by moebob24 on 2015-11-07
I did notice this :)

Thank you for the explanation.

I'll put my money on groupadd and addgroup being the same thing?

---

### Post by bab1 on 2015-11-07
> **moebob24 said:**
> 
I'll put my money on groupadd and addgroup being the same thing?

Yes.

See this from the adduser man page```
DESCRIPTION
       **adduser**  and  **addgroup**  add  users and groups to the system according to command line
       options and configuration information  in  /etc/adduser.conf.   [B][I]They  are  friendlier
       front  ends  to  the  low level tools like useradd, groupadd and usermod programs, by
       default choosing Debian policy conformant UID and GID values, creating a home  direc&#8208;
       tory  with  skeletal  configuration,  running  a  custom  script, and other features.
       adduser and addgroup can be run in one of five modes:[/I][/B]

```

---

