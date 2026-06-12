---
title: "[SOLVED] password change"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-08-29
Bs'd

How do I change my main login password in Ubuntu?

---

### Post by tangibleorange on 2008-08-29
> **Carnivorum said:**
> Bs'd

How do I change my main login password in Ubuntu?

have you forgotten your password and can't get in or are you trying to change it while logged in?

---

### Post by Oldsoldier2003 on 2008-08-29
reboot and select the recovery option from the grub menu. it will log you in as root:

from there :

```
passwd <your_username_>
```

then reboot:

```
reboot now
```

edit: this was based on the assumption that you cannot login at all to change your password. If you can log in then you can use the gui tool to change your password. system>administration>Users and Groups

---

### Post by Carnivorum on 2008-08-29
Bs'd

I'm logged in at the moment, I want to change my password while logged in.

---

### Post by Skorzen on 2008-08-29
```
man passwd
```

---

### Post by Joeb454 on 2008-08-29
Then use System > Administration > Users & Groups :)

---

### Post by tangibleorange on 2008-08-29
> **Carnivorum said:**
> Bs'd

I'm logged in at the moment, I want to change my password while logged in.

in that case, go to a terminal and do:

```
passwd *myusername*
```

you should then be asked for a new password. hope that helps!

---

### Post by Carnivorum on 2008-08-29
Bs'd

I managed to change it.  Thanks everybody!

---

