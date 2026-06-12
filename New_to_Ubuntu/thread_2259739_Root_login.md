---
title: "Root login"
date: 2015-01-06
forum: New to Ubuntu
---

### Post by anil8 on 2015-01-06
[FONT=arial]when i always use su for root login, i am going to always helpless[/FONT]
[FONT=arial]> and get some unidentify results like this---------[/FONT]
[FONT=arial]>[/FONT]
[FONT=arial]> nuggets@ubuntu:~$ su Password: Cannot execute q: No such file or[/FONT]
[FONT=arial]> directory nuggets@ubuntu:~$ su Password: su: Authentication[/FONT]
[FONT=arial]> failure nuggets@ubuntu:~$[/FONT]
[FONT=arial]>[/FONT]
[FONT=arial]> i am not getting any results, please go through this problem and[/FONT]
[FONT=arial]> give the solution.[/FONT]
[FONT=arial]>[/FONT]
[FONT=arial]> Thank you.[/FONT]

---

### Post by yancek on 2015-01-06
Use sudo instead of su.  Details at the Ubuntu site below.  Did you create a separate root user because it is not the default on Ubuntu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oldos2er on 2015-01-06
```
sudo -i
```

---

### Post by anil8 on 2015-01-06
i also used sudo instead, but still not working. and yes i created separate root user to install hadoop but always throw error.

---

### Post by alfred8 on 2015-01-06
Hi,

Have you done sudo passwd and created a password for root?

Once you do that, try su and type in the password you created.

Regards,

Alfred

---

### Post by bab1 on 2015-01-06
> **anil8 said:**
> i also used sudo instead, but still not working. and yes i created separate root user to install hadoop but always throw error.
You can't create a separate "root" user.  There is only one root user.  

You can have an administrator with the abllity to execute routines as the root user, but that is something different.

---

### Post by lisati on 2015-01-06
> **anil8 said:**
> i also used sudo instead, but still not working. and yes i created separate root user to install hadoop but always throw error.

Please provide some more information on the error message you saw when you tried to use sudo.

You should not need to create a "root" user to install software for Ubuntu. If you are logged in to your computer using your "admin" account - the account created when you installed Ubuntu - using *sudo*, as previously advised, should work. It will ask you for your password. Type in your admin account's password, which won't be shown on the screen but which will still be accepted when you press Enter.

---

### Post by papibe on 2015-01-06
> **alfred8 said:**
> Hi,

Have you done sudo passwd and created a password for root?

Once you do that, try su and type in the password you created.

Regards,

Alfred
I recommend **[COLOR="#FF0000"]not[/COLOR]** doing this just yet. Both 'sudo command' for a single command, or 'sudo -i' for a permanent root prompt are the standard practices.

Additionally, you could use:
```
sudo su
```
Regards.

---

### Post by QIII on 2015-01-06
Please refer to the the [RootSudo]("https://help.ubuntu.com/community/RootSudo") page for the full story.

---

