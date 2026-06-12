---
title: "installing problems"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by sakorty on 2012-08-07
Hi,
I am completely new to Linux so this may seem dumb to most of the people but anyways i was installing wine1.4 when my computer suddenly restarted. Now when i open the terminal and try to install wine1.4 again i get this error    "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"
And i get the same error if i try to install anything else. Plus there is like an error sign in the upper right corner which says i should run the package manager but i don't really know what that is. Please help me and thanks in advance.

---

### Post by Ravi5kumar on 2012-08-07
Remove the lock, run below commands in terminal [Press Ctrl+alt+t to bring up the terminal]:
  

```
sudo fuser -cuk /var/lib/dpkg/lock
``````
sudo rm -f /var/lib/dpkg/lock
```Now install what you want...:)

---

### Post by sakorty on 2012-08-07
It is working now, thanks a lot

---

### Post by Ravi5kumar on 2012-08-08
> **sakorty said:**
> It is working now, thanks a lot
You are welcome!

---

