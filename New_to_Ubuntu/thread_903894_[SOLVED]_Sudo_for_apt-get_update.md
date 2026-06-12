---
title: "[SOLVED] Sudo for apt-get update???"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by melbs on 2008-08-28
Do you have to be root to do an apt-get update? When I just type apt-get update it gives me:

```
melissa@melissa-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
melissa@melissa-desktop:~$ 
```I thought I never used to have to? Maybe I'm wrong...help?

---

### Post by tuxxy on 2008-08-28
Run the command as root yes, try

```
sudo apt-get update
```

---

### Post by melbs on 2008-08-28
Yes, that does work but do you HAVE to be root to run apt-get update?

---

### Post by nicedude on 2008-08-28
Yes you have to use sudo ( to elevate your permissions to ROOT ) to run any apt-get installation commands including update.

But always use sudo and never login as root to do things as you will end up with big troubles if you login as root instead.

---

### Post by melbs on 2008-08-28
Thank you both!

---

### Post by tuxxy on 2008-08-28
No problem, you also wont be able to log in as root unless you specified to allow this, so remember to sudo lol

---

