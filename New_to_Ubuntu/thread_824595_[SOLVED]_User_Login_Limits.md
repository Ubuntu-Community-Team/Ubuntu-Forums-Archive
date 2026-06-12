---
title: "[SOLVED] User Login Limits"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by MasterSushi on 2008-06-10
I am looking for a package that would allow me to designate specific time periods that a specific user could log into the system. And also if possible, force the user back to the switch user screen if they are on the system past the designated time period. Basically the idea is to set a time frame of lets say midnight to 8:00am where the user would be unable to get onto the system.

This is a feature set that Vista currently has that works rather well and my wife wants me to get Ubuntu setup the same way so that we don't need to worry about the kids jumping onto the computer in the middle of the night.

Any suggestions?

---

### Post by SunnyRabbiera on 2008-06-10
There are probably many tools for this, I know ubuntu christian edition has something like this.

---

### Post by Sinkingships7 on 2008-06-10
I'm pretty positive that a simple bash script could do this job, though I'm not the best bash programmer in the world. Or, hardly one at all.

---

### Post by SunnyRabbiera on 2008-06-10
I just wish i remember what the dang thing is called.

---

### Post by MasterSushi on 2008-06-10
I wouldn't know where to begin to make a bash script that could do this. Someone is bound to have created something to do this, at least I hope so. :)

---

### Post by Cypher on 2008-06-10
The following URL describes using PAM and CRON in conjunction to accomplish what you want. The document mentions FC6, but it's generic enough to work on Ubuntu. If you are using the Kubuntu variant, then the file /etc/pam.d/gdm that is described in the page won't exist.

Enjoy:
[http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/](http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/)

---

### Post by MasterSushi on 2008-06-10
This certainly looks like what I am wanting to accomplish. I will work at setting this up in the next day or two and report back.

---

### Post by MasterSushi on 2008-06-11
This works perfectly. Thank you so much for finding this.

---

### Post by cariboo on 2008-06-11
If you go to System-->Administration-->Login Window and click Security, you will see Enable Timed Login. I  think this is what you are looking for.

Jim

---

### Post by MasterSushi on 2008-06-12
> **cariboo907 said:**
> If you go to System-->Administration-->Login Window and click Security, you will see Enable Timed Login. I  think this is what you are looking for.

Jim

This setting designates a certain amount of time before an account is automatically logged into the system, it does not allow you to designate times that a user can log into the system.

The method located at: [http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/](http://skindley.wordpress.com/2006/12/11/fedora-core-6-controlling-logins-by-time/) works wonderfully.

---

