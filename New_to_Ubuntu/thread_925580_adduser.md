---
title: "adduser"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by maskiepop on 2008-09-20
Hi.

How do I add a new user such that it has bash/cli history and cli completion (bash_completion)? Better yet, how do I modify an existing user such that it gets these features?

The initial admin user account has the above features; the new ones I have created doesn't.

TIA

---

### Post by Dr Small on 2008-09-20
That's odd. Well anyhow, the bash completion and history commands are used from .bashrc. Copy that file from your account into the new ones and it should work. The original .bashrc file should be in /etc/skel

Dr Small

---

### Post by maskiepop on 2008-09-22
> **Dr Small said:**
> That's odd. Well anyhow, the bash completion and history commands are used from .bashrc. Copy that file from your account into the new ones and it should work. The original .bashrc file should be in /etc/skel

Dr Small

Thanks for responding to my post. 

The additional users I have created do have a .bashrc in their home directory. I also did a comparison, using diff, of their .bashrc file with the original admin's .bashrc, and the comparison showed no differences.

Another thing, I have made one of the non-admin users part of the admin group, and now this user have all the above features. So it seems to me the problem boils down to: how do I create non-admin users with these features in their cli (history, bash_completion)?

By the way, I am using Ubuntu 8.04.

TIA

---

### Post by Nepherte on 2008-09-22
putting:
```
# Enable bash completion
if [ -f /etc/bash_completion ]; then
        . /etc/bash_completion
fi
```
in .bashrc should give you wanted behaviour.

---

### Post by maskiepop on 2008-09-24
> **Nepherte said:**
> putting:
```
# Enable bash completion
if [ -f /etc/bash_completion ]; then
        . /etc/bash_completion
fi
```
in .bashrc should give you wanted behaviour.

Thanks. I think this should do it.

---

