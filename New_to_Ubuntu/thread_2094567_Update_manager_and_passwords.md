---
title: "Update manager and passwords"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by columbus2012 on 2012-12-14
Hi I've searched the faq's but not found an answer to the following.

(I'm running 12.04lts )
I thought Linux/Ubuntu _always _asked for your password before installing upgrades / new packages. 
I've just run update manager today and it installed 13, (I think), upgrades without asking for a password. Is this OK? 

I thought passwords were the root basis of Linux security.
Being a long time Windows user I am paranoid about viruses.

---

### Post by mcduck on 2012-12-14
Current versions of Ubuntu allow updating of certain applications without having to provide the password. 

Adding new packages, updating important system packages and other more critical package management tasks still request for password confirmation.

The idea is that since the packages come from trusted sources (why would anybody add a software source that can't be trusted ;))and the updates are mostly just bug and security fixes instead of major changes, there should never be a reason not to install them as, and to improve security it would make sense to make the update as easy and simple as possible, and to allow even non-admin users to apply such updates. After all installing them would be much less of a security issue (if any) than not having the system up-to-date and all security updates installed.

---

### Post by Cheesemill on 2012-12-15
This feature was introduced in 11.10.

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)

---

### Post by Frogs Hair on 2012-12-15
Kernel updates still have a password prompt.

---

