---
title: "Access denied after adduser"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by Youri_van_Dijk on 2014-02-12
Hey guys I've just created a new user and entered the password when it said enter UNIX password (correct right?).
After that I've established another connection, but access is denied. Why!? :D

---

### Post by Iowan on 2014-02-12
What do you mean by "established another connection"? Logged in (or attempted) as the new user?
You can check */etc/passwd* to see if the user got created.

---

### Post by Youri_van_Dijk on 2014-02-12
Thanks. Yes I meant that I had opened a new putty screen to login as the new user. I've checked the file and the user is indeed listed!

---

### Post by deadflowr on 2014-02-12
How'd you make the new user?

Command line or with a gui.
And if a command line, what command?

---

### Post by Iowan on 2014-02-12
> **Youri_van_Dijk said:**
> Thanks. Yes I meant that I had opened a new putty screen to login as the new user. I've checked the file and the user is indeed listed!PuTTY? So you're trying to log in via SSH? Is the machine running a(n) SSH server?

---

### Post by Youri_van_Dijk on 2014-02-13
Ah wait... I've installed open SSH and am running everything from command line. I've created the user with 'sudo adduser'

I remember following the advice in a tutorial to put 'AllowUser example' in the SSH config file for security. I've added my regular account (not using root) so probably the new user is denied since I have to add it to the SSH config? How would I do that best? Add another line to sshd_config with AllowUser newaccount or should I simple separate those with a space or comma on the existing line?

edit: I've removed the line for now, which resolves the error. I believe that simply adding extra users separated with a space should be sufficient as well.

---

