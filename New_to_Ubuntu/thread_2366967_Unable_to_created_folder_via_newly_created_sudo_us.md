---
title: "Unable to created folder via newly created sudo user"
date: 2017-07-24
forum: New to Ubuntu
---

### Post by jasonestibeiro on 2017-07-24
I created a user name `sysadmin`, added it to the `sudo` group and then did `su sysadmin` and switched to user `sysadmin`.

But now I want to create a folder but I get a message permission denied. Why is that? What am I missing here?

---

### Post by TheFu on 2017-07-24
Being in the sudo group is just a setup aspect. It doesn't make it have elevated rights until specifically requested - using the sudo command.

Also, using "su sysadmin" retains the environment from the prior userid.  If you want to use the environment for the sysadmin account, use **su - sysadmin**.

Always remember, Linux is a multi-user OS and that processes run with an effective userid and an effective groupid.  That applies to shells (which is just another process) too.

---

### Post by wildmanne39 on 2017-07-24
*Thread moved to **New to Ubuntu**.*

---

