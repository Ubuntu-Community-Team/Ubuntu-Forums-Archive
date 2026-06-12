---
title: "I'm a fool who forgot his password and/or username"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by ramunenke on 2008-08-11
I have ubuntu as a partition but I haven't logged into Ubuntu in a month. How can I recover my info because  I dont want to reinstall again.

---

### Post by Vadi on 2008-08-11
Try this:

> When Ubuntu boots, select Esc for the boot menu (Grub) and select recovery mode. Ubuntu will then boot w/o asking you for a password signed in as root. Type *passwd USERNAME* and it will reset your password. Let me know if this doesn't work :)

---

### Post by Vivaldi Gloria on 2008-08-11
> **ramunenke said:**
> I have ubuntu as a partition but I haven't logged into Ubuntu in a month. How can I recover my info because  I dont want to reinstall again.

1) When boot starts select Esc for the grub boot menu.

2) Select recovery mode. Ubuntu will then boot and log in as root. 

3) Type 

```
passwd <your_username>
``` 

and it will create new password. 

I assumed that you remember your username.

---

### Post by tuxxy on 2008-08-11
At boot select recoverymode from grub, now you should be at a prompt with root privs, try change the password with

```
passwd master
```

or just make a new user

```
adduser newuser_name admin
```

So the newuser has admin privs also.

---

### Post by xzaverax on 2008-08-11
Hi, i may be wrong but i do not think that you can get the information without being able to login to Ubuntu. you could always reinstall it if you have no data you would not mind losing.

---

### Post by DirtyDawg on 2008-08-11
LOL, it happens to the best of us :)

---

### Post by pparks1 on 2008-08-11
> **xzaverax said:**
> Hi, i may be wrong but i do not think that you can get the information without being able to login to Ubuntu. you could always reinstall it if you have no data you would not mind losing.

Actually, with the recovery mode you can get in and you get in as root with no password being asked.  That's the primary reason that physical security is such a huge deal.  Anybody with physical access and a CD pretty much owns your computer.   Obviously other things like BIOS passwords and drive encryption may slow them down/stop them...but most people don't go to that extent.

---

### Post by .nedberg on 2008-08-11
You can find your password by using the ls in the home dir```
ls 1 /home
``` it will liste all home-folders of users, just pick yours from the list!

---

### Post by ramunenke on 2008-08-11
I would like to thank all of you benevolent bastards for all your help. I typing from my ubuntu partition right now. I followed Vadi's and Vivaldi's advice and it let me create a new password. Thanks.

---

