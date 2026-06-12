---
title: "Updates wont update?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Siouxsy on 2008-07-18
I am quite new to Ubuntu. I like it. But i have had a few problems. It says updates are available but when i click on it. It tells me 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have no idea what this means. Anyone able to tell me and how to resolve this problem. If so please tell me in small words, i am not THAT brainy when it comes to computers. Thanks. 

Oh also... On some sites like 'myspace' the music doesnt play. I installed the  flash thing. but i dont know what to do regarding myspace and the music on the site. any ideas?

Thanks in advance
x

---

### Post by Sef on 2008-07-18
Applications > Accessories > Terminal

type or copy and paste this code:

> sudo dpkg --configure -a

then type or copy and paste this code:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Siouxsy on 2008-07-18
Thanks i will try and do that now...
its doing something...
*tries to get updates*
Oh wow! 
THANKS SOOO much!!
Seems to be working now.
Thanks alot!

---

