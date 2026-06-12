---
title: "[SOLVED] Difference between su/gksu and sudo/gksudo?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by koji042 on 2008-07-23
I'm currently trying to learn how to use the command line and I was wondering what the difference between "su" and "sudo" as well as the difference between "gksu" and "gksudo". I know that the former two are for working in the terminal and the latter are for graphical apps, but otherwise, I don't understand how they're different. Can anyone please explain how they're different?

Thank you very much. :D

---

### Post by Oldsoldier2003 on 2008-07-23
> **koji042 said:**
> I'm currently trying to learn how to use the command line and I was wondering what the difference between "su" and "sudo" as well as the difference between "gksu" and "gksudo". I know that the former two are for working in the terminal and the latter are for graphical apps, but otherwise, I don't understand how they're different. Can anyone please explain how they're different?

Thank you very much. :D

su can be used to change user. sudo is a command that allows you to execute (act) as the superuser or "root" user. For a more in depth explanation of the differences between sudo and gksu/gksudo see this [link]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by Bachstelze on 2008-07-23
su stands for "switch user", and will let you... switch users ;)

```
firas@iori ~ % su shs
Password:
shs@iori firas %

```

Here, I was logged in as "firas" and using su, I switched to "shs" without have to logout and log back in.

sudo, on the other hand, lets you (if you are permitted to do so) run commands as though those commands were run by another user, but without actually switching the current user :

```
firas@iori ~ % whoami
firas
firas@iori ~ % sudo -u shs whoami
shs

```


The most common usage of those commands is to allow usage of the super-user account ("root"). Note, however, that you cannot use su to switch to the root user in Ubuntu, and must therefore use sudo.

---

### Post by Bachstelze on 2008-07-23
> **Oldsoldier2003 said:**
> sudo is a command that allows you to execute (act) as the superuser or "root" user.

...or any other user (once again, if permitted). Please read above.

---

