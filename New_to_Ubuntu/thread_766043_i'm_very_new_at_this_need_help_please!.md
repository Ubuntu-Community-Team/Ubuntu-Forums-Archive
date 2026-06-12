---
title: "i'm very new at this need help please!"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by imgreen on 2008-04-24
i just installed ubuntu 7.10. i tried to to do updates, when i put in my password, it says i am not an administrator. also, the synaptic is not there. after i installed the 7.10 what do i need to do next? it seems like i got a partial version, but i know i downloaded the whole thing. i did a partition with the windows XP. also, when i try to do anything in the terminal, i cant seem to do anything, no matter what codes i try to use. i am thinking of just replacing the whole 7.10 with the new release. need help please, what do you guys think?

---

### Post by rouge568 on 2008-04-25
I would do a fresh install, but make sure you back up your data, and triple check your partitioning so you don't erase XP.

---

### Post by Paqman on 2008-04-25
> **imgreen said:**
> i just installed ubuntu 7.10. i tried to to do updates, when i put in my password, it says i am not an administrator.

Do you have multiple users on the machine?

By default, the first user is an administrator, but subsequent ones aren't. If you go into System > Admin > Users & Groups see if your account has permission to administer the system.

---

### Post by imgreen on 2008-04-25
thanks guys, i am the only user, and i tried that also, when i try to go to the admin>, i cant find the users & groups.

---

### Post by Paqman on 2008-04-25
Ugh, sounds like it's dropped you from the admin group somehow.

Can you reboot into recovery mode? If so you can give yourself admin powers
```

sudo nano /etc/group

```

You want to add yourself to both admin and adm groups, I believe.

---

