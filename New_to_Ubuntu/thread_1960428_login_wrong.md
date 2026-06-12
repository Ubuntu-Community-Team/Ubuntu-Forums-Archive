---
title: "login wrong"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-04-17
I have set up an old laptop on xubuntu 11.10. It works OK but insists on logging in to the admin account automatically. I have it set to only login to the guest account automatically-without password. How do I fix this?

---

### Post by 2F4U on 2012-04-17
Not sure how you configured it but you may wish to look at this tutorial:

[http://www.liberiangeek.net/2012/01/enable-automatic-guest-login-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2012/01/enable-automatic-guest-login-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by cmcanulty on 2012-04-17
I went to users and groups and set librarian to not auto login and set guest to auto login with no password. It does the opposite. So when powered on it goes auto to librarian account not asking for a password. I want it to do as I set up in users. So guest account auto logs in without password.This is xubuntu but the users seems setup the same as ubuntu it just doesn't seem to work.This command also doesn't work. I may have caused some confusion I am not talking guest but I made a user called guest. I will change that to something else. But the problem is it auto logs in to the admin account (librarian) and I can't have that happen at the library.
```
librarian@Darcy31:~$ sudo gedit /etc/lightdm/lightdm.conf
sudo: gedit: command not found

```

---

