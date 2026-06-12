---
title: "[SOLVED] cant open synaptic manager"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by misswham on 2008-11-06
when i try to open it i get this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what can i do step by step

---

### Post by drs305 on 2008-11-06
Open a terminal: (ALT-F2), type in the code below, tick 'Run in terminal'. When it asks for your password, type it in and ENTER. You won't see the characters as you type your password.

You must run it with administrative powers:
```
sudo dpkg --configure -a
```

---

### Post by superprash2003 on 2008-11-06
just type that command in the terminal and it would solve your problem.. add a sudo before the command if required..

---

### Post by Jammy4041 on 2008-11-06
I did this when trying to install flash, but I interrupted it. Type, as it says, 

```
sudo dpkg --configure -a
```

and an 

```
sudo apt-get install -f
```

should help clear up any repository problems that you might encounter with synaptic as well.

hope this helps.

---

