---
title: "I can not get intoUbuntu as admin. My password never works"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by mangelperez on 2014-01-05
I have problems with the administrator password. When I write it in to start a season, the system gives me no error message, but I return to the same home screen. I followed the steps to recover at the start and when I use the command "passwd user", to enter the same password a second time, the system tells me that he could not make the change ...When I need the password to add an aplication or so, the system do recognize the password! I would aprecciate so much your help.-

---

### Post by r3dd on 2014-01-05
As in, you are trying to log in with root? Or an account that has administrator rights?

Root is disabled for login so you wouldn't be able to log in using it.

If you are trying to change the password of another account, us "sudo passwd <user>".

If you are trying to change the password to your own account, just use "passwd".

The account you made initially will be the admin password you should be using when you install software. Just use "sudo" in front of the commands you want to execute with admin rights. There should really never be a point when you need to use the root account for normal operations.

---

