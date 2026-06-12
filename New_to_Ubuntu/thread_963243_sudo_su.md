---
title: "sudo su"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by jsshere on 2008-10-30
what does sudo su mean?

---

### Post by igknighted on 2008-10-30
it gives you superuser priveleges without using sudo until you close the session.  It has (almost) no use for 90% of users, so it is not recommended that you use it.

---

### Post by itisbasi on 2008-10-30
That's the terminal command to assume root privileges.

---

### Post by spiderbatdad on 2008-10-30
The command is unsupported in Ubuntu. It requires unlocking the root password.
Instead use sudo -i for a root session.

See here for more info:[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also this forum has a policy against advising sudo su.

---

### Post by macogw on 2008-10-30
> **spiderbatdad said:**
> The command is unsupported in Ubuntu. It requires unlocking the root password.
Lies.  Putting sudo before su means that the root password does not need to be set.  It's only for just-plain "su" that that's the case.

---

### Post by ufis on 2008-10-30
> **spiderbatdad said:**
> See here for more info:[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thank you.
Useful page to read. Now I know the difference between sudo -s and sudo -i.

---

### Post by thomaswp on 2009-01-24
Does this mean any random user can gain root access when sitting in front of my machine without using a password?

If it does, which password should I have set up and when, and how can I fix it?

Mind you I cannot believe that it does mean that - it just seems too madly insecure, so I imagine it is my ignorance here.  I have done a bit of searching on this but am none the wiser.

---

### Post by SunnyRabbiera on 2009-01-24
> **thomaswp said:**
> Does this mean any random user can gain root access when sitting in front of my machine without using a password?

If it does, which password should I have set up and when, and how can I fix it?

Mind you I cannot believe that it does mean that - it just seems too madly insecure, so I imagine it is my ignorance here.  I have done a bit of searching on this but am none the wiser.

It shouldnt, but still change your password okay?
Also no auto logins either :D

---

### Post by Cosimix on 2009-01-24
You use it when root account is locked (Ubuntu default). 
**sudo -i** does the same thing, drops you in a bash with root permissions

---

### Post by 3rdalbum on 2009-01-24
Sudo means "run this next bit as root".

Su means "Switch user". If you don't specify a user to switch to, it assumes you want to switch to root and asks for root's password.

When you run them in combination, you are running the "su" program as root, and telling it to switch to root; that's why "su" itself doesn't ask for a password.

You could also do "sudo sh". That would run Bash as root. But for some reason we tend to do "sudo su", probably out of social inertia :-)

---

