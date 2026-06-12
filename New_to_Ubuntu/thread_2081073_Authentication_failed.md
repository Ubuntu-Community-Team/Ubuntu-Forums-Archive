---
title: "Authentication failed"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by kaivy on 2012-11-05
New linux user and unable to upgrade from ubuntu 10.10 to 11.04 in Dell inspiron n4050, i receive this messge:

 Authentication failed
 Authenticating the upgrade failed. There may be a problem with the network or with the server.

  if u can help me, I shall b very thankful.


regards,
kaivy

---

### Post by BBQdave on 2012-11-05
> **kaivy said:**
> New linux user and unable to upgrade from ubuntu 10.10 to 11.04 in Dell inspiron n4050...

I would humbly offer that you should back up your data and do a fresh install of 12.04LTS or 12.10. Depending on the strength of your graphics, and since you are coming from 10.10, you may want to check out **Xubuntu** :D

---

### Post by Bashing-om on 2012-11-05
kaivy; Hi ! Welcome to the forum.

Let's see if the fault can be isolated to the network or your system.
from terminal post the out put of terminal codes:
```
sudo apt-get update
sudo apt-get upgrade
```Depending of out put -> what happens next. ==> BDQ

---

### Post by Wim Sturkenboom on 2012-11-06
One thing might be that you're too late to do this upgrade ;) Support for 11.04 stopped with the release of 12.10. So the repositories might have been moved.

I agree with BBQdave that you're better of doing a fresh install of something recent because, after 11.04, you need to upgrade to 11.10 (that will only be supported for another 6 month).

Just my thoughts.

---

### Post by kaivy on 2012-11-06
thanx a lot buddy... let me try my hand on 12.10 and i will get back to u

---

### Post by kaivy on 2012-11-06
as i m new to linux, i m not aware of these sudo codes. can u b more precise how to reach these commands...

---

### Post by Wim Sturkenboom on 2012-11-06
When logged in in the graphical environment, press <ctrl><alt>t (that is, press 't' while control and alt are pressed).
Type the command; it will ask for your password. Type it (you will not see anything, just type it) and press <enter>.

---

### Post by NikTh on 2012-11-06
> **BBQdave said:**
> I would humbly offer that you should back up your data and do a fresh install of 12.04LTS or 12.10. Depending on the strength of your graphics, and since you are coming from 10.10, you may want to check out **Xubuntu** :D
Hi
I agree too. 
Consider for a fresh install of 12.04 or 12.10. 
Thanks

---

