---
title: "user password/root password terminology"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by aef54 on 2012-10-03
This is question is purely about terminology.

I read this on wikipedia, in the article about "sudo"

> Unlike the su command, users typically supply their own [password]("https://en.wikipedia.org/wiki/Password") to sudo rather than the root password

Is there a difference between the user password and the root password?

I use Ubuntu and I only use one password to log in and  sudo commands. Is this the user password or the root password?

---

### Post by Elfy on 2012-10-03
It is the user password.

Root password is disabled by default.

---

### Post by aef54 on 2012-10-03
Okay. Is it true that you only need a specific root password when you have various users on a PC, while only the admin can have root access?

---

### Post by Elfy on 2012-10-03
The first user is given root rights through sudo.

Other users normally wouldn't - there's nothing to stop you giving them those rights though.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by newb85 on 2012-10-03
In some other Linux systems (Debian, for example), a user "root" is set up on install.  Other users can be given sudo privileges, but that isn't the default.

In Ubuntu, the "root" user isn't set up by default, but the first user set up is set as an administrator and given sudo privileges.

In either case, it can be changed to imitate the other.

---

### Post by aef54 on 2012-10-03
Thanks guys.

---

