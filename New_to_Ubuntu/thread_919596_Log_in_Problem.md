---
title: "Log in Problem"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Igniteflow on 2008-09-14
I've just managed to lock myself out of Kubuntu.  After installing it on my family's computer and making setting up a user account for each person, I deleted the account I was currently using and restarted.  Now when I boot up it gives me the list of user names which I can select, but won't allow me to log in.  I enabled passwordless log in, but when I hit return it just says "Log in failed".  This is the same story for all the user names.

Could somebody please tell me how I can get back into my system?

---

### Post by bobnutfield on 2008-09-14
You could boot into recovery mode (which is single user mode as root) and add yourself back as a user with a password.  You could at least then get back into the system try and correct whatever is wrong.  I can't imagine why your other users cannot log in if you enable passwordless log-in, but there is probably an issue with that.

---

### Post by k33bz on 2008-09-14
here, I googled it for you, top two links

[http://my.opera.com/Contrid/blog/show.dml/486617]("http://my.opera.com/Contrid/blog/show.dml/486617")

[http://www.linuxquestions.org/questions/linux-security-4/password-recovery-in-edubuntu-7.04-in-terminal-root-login-su-password-603463/]("http://www.linuxquestions.org/questions/linux-security-4/password-recovery-in-edubuntu-7.04-in-terminal-root-login-su-password-603463/")


these two sites were referring to Edgy and Dapper, but the same will apply to all Ubuntu Distros, might even work with all debian systems, dont know about that one for sure though.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi Igniteflow,

The account kubuntu created at installation has admin rights, removing it was a (bad) mistake.

So you will have to give admin rights to some account, and _that basically also means leaving a password for this one_.

So :

- Keep in mind that all the follwing steps will be done with admin privileges, messing one up can remove everything you have installed and kill your neighbour's dog.

- Boot into recovery mode, as Bobnutfield said.

- Give a password to an existing account :

passwd youruser

- Give this account rights to become admin :

Edit the group file :

nano /etc/group

Add yourself to the admin group, that is the group file should contain a line that looks like

```
admin:x:115:
```

(the number is not important), change it to

```
admin:x:115:youruser
```

- Reboot (type reboot)

Hope this works :)

---

