---
title: "no access to system configuration"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by cazmatazzz on 2008-04-26
hello! i just upgraded to hardy but i can't seem to get permissions to do anything from the system menu or in terminal, every time i try to do something that deals with system configuration it tells me that i dont have access to system configuration, 

when in terminal and i type for exampel sudo apt-get install update it tells me that dpkg was interupted, you must manually run 'dpkg --configure -a' to correct the problem

when i do that (dpkg --configure -a)it tells me that this can only be done by system administrator, 

before hardy there was only one user, which was the system administrator, after the upgrade it seems it got messed up and i dont know how to change it back

---

### Post by ibutho on 2008-04-26
If you need to do any sysadmin stuff, prefix the commands to be run with "sudo" e.g.
```
sudo dpkg --configure -a
```

---

