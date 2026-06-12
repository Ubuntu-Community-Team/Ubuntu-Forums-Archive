---
title: "problem with su"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by 1chad1 on 2008-08-19
I have been trying to log into the root but when I type my password I get 
chad@chad-desktop:~$ su
Password:
su: Authentication failure
chad@chad-desktop:~$
what is causing this is it a problem with my pass and if so hoW do I change it to correct this problem
Thanks

---

### Post by iaculallad on 2008-08-19
> **1chad1 said:**
> I have been trying to log into the root but when I type my password I get 
chad@chad-desktop:~$ su
Password:
su: Authentication failure
chad@chad-desktop:~$
what is causing this is it a problem with my pass and if so hoW do I change it to correct this problem
Thanks

By default, Ubuntu's root password is disabled (For security purpose). You can get root privilege just by inputing the command below on your terminal and USE your own password:

```
sudo -i
```

---

### Post by 1chad1 on 2008-08-19
great thanks very  much appreciated

---

