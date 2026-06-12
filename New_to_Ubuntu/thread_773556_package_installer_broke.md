---
title: "package installer broke"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by jason15417 on 2008-04-28
locked up package installer during limewire install now i cant use it to install anything but i get this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Report how? why cant i fix it :(

---

### Post by Monicker on 2008-04-28
> **jason15417 said:**
> locked up package installer during limewire install now i cant use it to install anything but i get this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Report how? why cant i fix it :(


This should work:
```

sudo dpkg --configure -a
```

---

### Post by jimrz on 2008-04-28
> **jason15417 said:**
> locked up package installer during limewire install now i cant use it to install anything but i get this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Report how? why cant i fix it :(
open a terminal and type
```
sudo dpkg --configure -a
```
when prompted for your password, type it and press enter,

---

### Post by jason15417 on 2008-04-28
yes it did ty so from now on if i given a code add sudo in front of it and it should work?

---

### Post by Oldsoldier2003 on 2008-04-28
> **jason15417 said:**
> yes it did ty so from now on if i given a code add sudo in front of it and it should work?

no. the reason you were told to run the command under sudo is because the command needs to run under root privileges. If you constantly use sudo you can easily mess up your system with an unfortunate typo, since you wont have file permissions protecting you.

---

### Post by Xiong Chiamiov on 2008-04-28
Sudo (stands for super-user do) is used to give root priviledges to some command.  It's not good to sudo everything, but many administrative tasks require it.  Usually, if you see something like "permission denied", then you need to sudo it.

---

### Post by schauerlich on 2008-04-28
sudo gives you permission to do a lot more things than you usually can by default. See this page for more details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jason15417 on 2008-04-29
so sudo is only to be used if the super user error is given ok i got it now btw i only used linux for about 4 hours now so i know very little

---

