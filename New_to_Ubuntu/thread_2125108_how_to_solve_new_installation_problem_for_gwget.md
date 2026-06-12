---
title: "how to solve new installation problem for gwget"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by theswapneil on 2013-03-13
when i am using command

 sudo apt-get install gwget

i m seeing this error. Please tell me how to solve this problem.

I am new to ubuntu


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by mellocode on 2013-03-13
This error indicates that their is potentially another administration tool running. Do you have additional drivers or the ubuntu software center open?

---

### Post by siddharth007 on 2013-03-13
You can delete the lock file with
```
rm /var/lib/apt/lists/lock
```

you may also need to delete the lock file in the cache directory
```
rm /var/cache/apt/archives/lock
```

You need to be a 'sudo' user before executing these commands.

---

