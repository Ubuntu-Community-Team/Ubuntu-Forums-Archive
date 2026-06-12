---
title: "Problem with AutoUpdate"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by uboom on 2008-05-19
I install Ubuntu 8.04 (Hardy) on and old Computer at work, and everything is working fine.
Except for the fact that when I try to update or do any king of task that requires you to enter the password for the root or the user with administrative priviledges, it does't appears.  You can see in the status bar that there is a program "Starting Administrative Application" but it goes away without asking you for the password and the application that requires the authorization hangs up.

Please let me know how can you help me.


Ulises Boom
TERRACHEM
Dominican Republic

---

### Post by mike555 on 2008-05-19
If you mean the password doesn't show , it isn't suppose to ....... just carefully type in the password and click enter .......

---

### Post by uboom on 2008-05-19
No, what i meant is that the screen where you are supposed to enter the password doesn't show up.

Thanks


Ulises Boom

---

### Post by Kevbert on 2008-05-19
You could try the following from terminal:
```
sudo apt-get update

```
as a short term solution.

---

### Post by uboom on 2008-05-19
Thanks for that, I try the sudo apt-get update
It seems to get all the information for update but it keeps poping up an icon for the updates to be install.

Also, when I try to run any application that needs the administration password or the password for authorization, it doesn't appear the windows asking me for the password.

I don't know if I change something by mistake or with some of the autoupdate change anything without me knowing about it.

Thanks

---

### Post by Kevbert on 2008-05-20
Another command you could try from terminal:
```
sudo apt-get install -f
```
This will repair any installed, but damaged packages.  Then try Synaptic again.

---

