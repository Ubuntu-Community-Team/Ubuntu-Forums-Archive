---
title: "root password"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by poscomp on 2008-07-25
When I installed the system, I typed the wrong password. I was able to change it for me as a user but am having problems changing it for root login. Also, su doesn't recognise the incorrect password as correct for su. Can anyone help me, please. Thanks.

---

### Post by t0p on 2008-07-25
Are you sure you set a root password when installing?  Reason I ask is, by desfault Ubuntu does not ask you to set a root password.  If you need to do a task that requires you to have root privileges, just prefix the command with **sudo**.

---

### Post by argail1980 on 2008-07-25
by default, ubuntu has the root-account disabled.
If I get you right, you can login as user with your new(correct) password, but not do sudo?
Or is it that sudo works, but to login as root does not?

have a look at /etc/sudoers

```
sudo nano /etc/sudoers
```

there should be a line starting with "Defaults". the flag "rootpw" in that line will require the sudo user to type the actual root password instead of his own. DO NOT ENABLE THIS IF YOU DON'T HAVE SET A ROOT PASSWORD.
If that flag is already set, remove it and the user will be ale to sudo with his own password.

---

