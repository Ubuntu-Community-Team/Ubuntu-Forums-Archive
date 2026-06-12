---
title: "[SOLVED] Removed Self from sudo list"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by zackf on 2008-07-13
In trying to add myself to a new group I forgot to add the -a option, now I have no sudo power. I am the only user on my install, so now I have no sudo power. Am I hosed?

Zack

---

### Post by Bachstelze on 2008-07-13
Boot in recovery mode and add yourself back ;) Just copy the line about root, replacing root with your login, like

```
# User privilege specification
root    ALL=(ALL) ALL
firas   ALL=(ALL) ALL

```

I like to do it that way, because it gives sudo access to my account and I don't have to worry about groups.

---

### Post by zackf on 2008-07-13
Too easy. Thanks!

---

### Post by aysiu on 2008-07-13
While this worked, since you are the only user on the system, I thought I'd just put out there that this isn't technically the proper way to fix the problem, just on the off-chance that you do add other users later.

You really shouldn't have to edit the /etc/sudoers file every time you want to add someone to the *admin* group. The /etc/sudoers file should let *admin* users perform root functions with *sudo*, and then you can use System > Administration > Users and Groups to add or subtract people from the *admin* group.

More details here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Bachstelze on 2008-07-13
> **aysiu said:**
> While this worked, since you are the only user on the system, I thought I'd just put out there that this isn't technically the proper way to fix the problem, just on the off-chance that you do add other users later.

Very true. It is, however, a good way to prevent problems similar to the one zackf faced. Since full sudo access is given to the user regardless of groups, it will ensure it is not lost due to such mistakes. Of course, one can still also add a group afterwards.

---

### Post by bab1 on 2008-07-13
On a philosophical level, should we ever give advice that circumvents the proper running of the system.  Making mistakes and  recovering from them is how we learn.  Altering the system to prevent errors causes poor habits.  One could make use of the .bash_aliases file for a safety net.

I chide...because I can.  You do all of us a great service.  :D

---

### Post by zackf on 2008-07-14
Had I used System > Administration > Users and Groups from the beginning that probably wouldn't have happened anyway. I thought I was hot stuff with the CLI ;-)

---

### Post by Bachstelze on 2008-07-14
> **bab1 said:**
> On a philosophical level, should we ever give advice that circumvents the proper running of the system.  Making mistakes and  recovering from them is how we learn.  Altering the system to prevent errors causes poor habits.

Complete rubbish. Just because Ubuntu sets thing up one way by default doesn't make it the supreme truth. Could you please explain me how my advice "circumvents the proper running of the system"? It does not. I wish people would stop thinking that everything that is not done The Holy Ubuntu Way is evil and dangerous.

I know what I'm doing, and I know what I'm telling others.

---

