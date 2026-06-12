---
title: "Brand new 15.10 Mate install will not let me login"
date: 2015-11-25
forum: New to Ubuntu
---

### Post by teknopaul on 2015-11-25
I create a user during the installation procedure but when I boot the MATE GUI it will not accept my password, for my normal user or root.

I'm 100% sure the passwords are correct, I can login with SSH using the passwords.

sudo pam_tally2 --user=myuser
Login           Failures Latest failure     From
myuser           0    

Any other ideas?

---

### Post by teknopaul on 2015-11-25
Looks like this Ubuntu  MATE install is DOA, kind of annoying took hours and hours to install. 
Seems pam config is borked,  "no such file or directory" errors in /var/log/auth.log.

This is my 5th messed up Ubuntu 15.10 install for different reasons.  A base install from scratch onto a new harddisk fails.

---

### Post by Bashing-om on 2015-11-25
teknopaul; Hello; Welcome to the forum .

Maybe a graphics driver  issue (?).

What returns:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

New hardware, and perhaps the driver just is not in the software repository .

[INDENT][INDENT]maybe
[/INDENT][/INDENT]

---

### Post by QIII on 2015-11-25
Hello!

A quick run-down on your entire hardware spec might be very helpful.

I would also say that taking "hours and hours" to install indicates something not being right.  An installation should take under 30 minutes.  Can you tell us about how you were doing the installation?

---

