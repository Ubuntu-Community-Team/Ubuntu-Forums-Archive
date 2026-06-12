---
title: "Guest Account"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by powder on 2011-09-07
In 11.04 the Guest Account does not have the necessary privileges to access /home.  However, I noticed in 11.10 beta the Guest Account does have read access to /home.  Is this a bug or a feature? :confused:

---

### Post by sanderd17 on 2011-09-07
Aren't new files always rw-r--r--? So that anyone can read them?

---

### Post by powder on 2011-09-07
The permissions of /home on 11.04 and 11.10 are exactly the same (drwxr-xr-x).  Despite /home having the same permissions in both releases, one Guest Account has read access while the other does not.  For this reason I think the Guest Account must have its own set of permissions.

---

### Post by jbicha on 2011-09-07
> **powder said:**
> In 11.04 the Guest Account does not have the necessary privileges to access /home.  However, I noticed in 11.10 beta the Guest Account does have read access to /home.  Is this a bug or a feature? :confused:

Why don't you open a bug and find out? :-)

---

### Post by powder on 2011-09-07
[https://bugs.launchpad.net/ubuntu/+bug/844219](https://bugs.launchpad.net/ubuntu/+bug/844219)

:)

---

### Post by Larkspur on 2011-09-07
> **powder said:**
> [https://bugs.launchpad.net/ubuntu/+bug/844219](https://bugs.launchpad.net/ubuntu/+bug/844219)

:)

I think you should mark this as a security bug, since anyone using the guest session has access to user files, which is what it was created to avoid.  How do you do that?  No idea; the only way I know of is to tick the button when the report is being created.

---

### Post by mc4man on 2011-09-07
Personally think it's even a bit worse than that, though ubuntu doesn't agree.
Because of fast user switching a guest can also log into any other presently logged in user without a password. Don't see any obvious way to turn this off globally so if allowing a guest then better log out first.

---

### Post by powder on 2011-09-07
I thought about checking the security box but I think that's only for bugs that could result in escalated privileges.

---

### Post by Larkspur on 2011-09-07
> **powder said:**
> I thought about checking the security box but I think that's only for bugs that could result in escalated privileges.

I think it still counts as a security bug, especially if what mc4man is true.  Also, you say in your bug that you don't know what program to file it against.  I'm pretty sure it's gdm-guest-session.  I don't know how to switch it; like you, I'm pretty new to this bug reporting game.:p

@mc4man: it gets worse again, at least for me: I don't have an apparmor profile for gdm-guest-session; I can't see it when I run sudo aa-status, and it doesn't appear in /etc/apparmor.d.  Has everyone else got it? And/or am I imagining there ever was one?

---

### Post by powder on 2011-09-07
Larkspur:  AFAIK gdm was replaced by lightdm in 11.10 so I was leaning toward lightdm.  Either way, I'm sure the devs will take care of it so I'm not too worried about it.

mc4man:  It may be safer to just remove the Guest Account unless the devs can lock it down by release.  Though, I still haven't tested removing it yet...

---

### Post by powder on 2011-10-07
This bug is now fixed.

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/849027](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/849027)

---

