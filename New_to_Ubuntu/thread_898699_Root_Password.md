---
title: "Root Password"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by G!zZm0 on 2008-08-23
How can I know if I already have a root password or not??? If I dont have one, how can I create one??? Any help?????

---

### Post by terry123b99 on 2008-08-23
your root password is the password you chose when installing ubuntu as far as am aware :)

---

### Post by tuxulin on 2008-08-23
in addition to terry123b99
the default ubuntu user can become root.

for example 
when you type "sudo commands <-args>" then your password you will become root automatically to execute the command, once complete your back to the normal user.

open your terminal, you will see something like
username@local-machine:~$ (notice the **~$**) this is normal user

another example (**not** recommended to do work with)
type sudo bash, put the password in now you will see something like
root@local-machine:~#  (notice root get ~#)

was this a bit too much  hmmm
Tuxulin

---

### Post by Joeb454 on 2008-08-23
Instead of root, Ubuntu uses "sudo"

Please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information :)

---

### Post by t0p on 2008-08-23
Ubuntu does not deal with root opasswords as such.  The user account you set up during installation had administrative permissions.  If you want to do a command that requires root permissions, you should prefix the command with "sudo", eg

```
sudo apt-get install somepackageorother
```

The computer will ask for your password - so **you type in the password for that account.**

---

### Post by aysiu on 2008-08-23
If you have to ask if you have a root password set, I can guarantee you you don't need to set one or ever log in as root.

Why don't you tell us what you think you need a root login for, and we'll tell you the proper (and honestly probably more convenient) way to do it?

---

