---
title: "A crippling password problem"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by chrlywtrfall on 2011-11-08
I may have made a fatal mistake.

I just installed 11.10 from CD.

From the 'User Accounts' screen I changed the password field to 'none' thinking that it wouldn't ask me for a password anymore.

But it does still ask for a password. For everything. My old password doesn't work. Now I can no longer install software or do anything in terminal. I can't even unlock the 'User Accounts' screen to make a new password. 

Is there anything I can do besides re-install?

Help me please and thank you.

---

### Post by 1clue on 2011-11-08
Your password is probably "none" now.

Pop up a command prompt.  Type 'passwd' and then hit enter.

If that doesn't work, you can go to [http://www.sysresccd.org](http://www.sysresccd.org) and make an iso image.  This is a wonderful tool that you really should have a copy of no matter what computer you own.

Boot off that, mount your / partition, chroot into it and then change your password again.

---

### Post by TeoBigusGeekus on 2011-11-08
Boot up into recovery mode and once in the root console, give
```
passwd root
```
to give a new password for the root account.
Post back with the outcome.

---

### Post by chrlywtrfall on 2011-11-08
Thanks 1clue. I think that worked.
I can do stuff now.

---

