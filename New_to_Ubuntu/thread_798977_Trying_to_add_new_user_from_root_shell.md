---
title: "Trying to add new user from root shell"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by sfrtbr on 2008-05-18
I don't remember the password and username for my one-and-only user account. I booted into a root shell to add a new user, but Ubuntu informed me that I would have to load "usr/sbin/useradd" in order to do so. What should I do?

---

### Post by Mr. Svinlesha on 2008-05-18
Do you by any chance have a dual-boot?  If so try this:

Restart 

at the GREB screen, select &#8220;recover mode&#8221; (latest kernal) 

type: cat etc/passwd | grep 1000 

It should allow you to recover your user name and password without logging in as root.

Hope that helps.

---

### Post by N.N. on 2008-05-18
Just type the following command: ```
adduser
``` You'll then have to answer a number of questions regarding the user (login name, UID, groups, home directory, shell, and expiry date). You'll also have to enter a password for the new user.

---

