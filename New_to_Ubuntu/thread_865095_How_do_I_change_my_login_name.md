---
title: "How do I change my login name?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Jamface on 2008-07-20
I am the administrator for a dual installation.  The name below /home/ I chose when I installed Ubuntu is not now appropriate.  How do I change it?

---

### Post by Canis familiaris on 2008-07-20
> **Jamface said:**
> I am the administrator for a dual installation.  The name below /home/ I chose when I installed Ubuntu is not now appropriate.  How do I change it?

I dunno whether you can change your login name, I dont think you can though.
But you can create a new user and delete the previous one. Make sure add your new user to group admin so that you can have administrator priviledges.

Go to System->Administration->Users & Groups

---

### Post by nick_h on 2008-07-20
Have a look at the *usermod* command:
```
man usermod
```

You can change the login name with the -l option and the home directory with the -d option.

---

