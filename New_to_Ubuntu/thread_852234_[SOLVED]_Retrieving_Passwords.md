---
title: "[SOLVED] Retrieving Passwords"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by webbdawg on 2008-07-07
I normally log on as a limited user because I have an administrative account too. But I seem to have misplaced the admin password. I have tried many iterations of it, but it fails.

I have gone to the Administration>User/Groups CP but have not been able to get the issue resolved.

How do I retrieve user passwords?

I am not experienced with the terminal either.

---

### Post by sisco311 on 2008-07-07
Reboot in Recovery Mode and change the 
password from the root shell:
```
passwd [I]username
[/I]exit
```

---

### Post by webbdawg on 2008-07-07
Thanks, it's good to know.

I figured out what I was doing wrong. I had changed the name of the root account (not the login). I was trying to use that instead of the login .

---

