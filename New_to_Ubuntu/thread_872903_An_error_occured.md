---
title: "An error occured:"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by vissari on 2008-07-28
when i try to install something via: Applications>Add/Remove... is saying:

An error occured:

E:dpkg was interrupted, you must manually run 'dpkg --configure - a' to correct problem.
E:_cache->open()failed, please report.


how to fix this please help. im absolute beginner in Ubuntu thing.

---

### Post by coffeecat on 2008-07-28
Open a terminal (Applications > Utilities > Terminal) and:

```
sudo dpkg --configure -a
```When asked for password, don't worry, it is going in. It just looks as though it isn't.

Useful Link:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**Edit:** Sorry - Applications > **Accessories** > Terminal. :oops:

---

### Post by eightmillion on 2008-07-28
Start a terminal. This is under accessories on the menu. Enter
> sudo dpkg --configure - a
and press enter. It will ask for a password. That should fix your problem

---

### Post by vissari on 2008-07-28
thank you very much now is OK.

---

### Post by Immolatus on 2008-07-28
It's telling you exactly what to do. Open a terminal: Applications-->Accessories-->Terminal 
Then type in the terminal: sudo dpkg --configure -a and press enter. 
should fix the problem.
Whats described here is like a log jam, there is a stalled installation jammed in dpkg so you need to clear it by re setting dpkg K?

---

