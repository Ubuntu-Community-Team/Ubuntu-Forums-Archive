---
title: "dpkg Error"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by drdivad on 2008-09-15
Hello all, I've successfully installed the OneLinux version of Ubuntu (a streamlined version specifically for the Acer Aspire One netbook)...

After installing I ran: 

> sudo apt-get update
sudo apt-get upgrade

however after running the upgrade (2nd line), I accidentally quit the terminal.. and now whenever I try upgrading or downloading a program (tried sudo apt-get install vlc), it gives me this error:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

after typing in dpkg --configure -a, I get the following message:
> dpkg: requested operation requires superuser privilege
I'm just started using Ubuntu so hopefully it's not too complicated.. thanks.

---

### Post by Oldsoldier2003 on 2008-09-15
> **drdivad said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```
sudo dpkg --configure -a
```

---

### Post by tuxxy on 2008-09-15
Adding a sudo to the start will run the command with super user privs

---

### Post by drdivad on 2008-09-15
Thanks fellas, worked like a charm.

---

