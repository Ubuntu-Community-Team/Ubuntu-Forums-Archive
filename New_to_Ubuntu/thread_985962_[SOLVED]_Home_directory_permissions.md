---
title: "[SOLVED] Home directory permissions"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Jacdeb6009 on 2008-11-18
I have a problem, for reasons I don't understand I suddenly have a problem when starting up Linux.  After entering the user name and password I get an error message as follows:

"User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's HOME directory must be owned by user and not writable by others."

Two questions:

(1) How do I correct this; and
(2) How could this have happened.

I can boot and access the system normally, but every time I boot, this happens.  Any ideas would be welcome.

I am running Ubuntu Hardy Heron and have been running it trouble free for about four months now and this "problem" has appeared which is quite a mystery to me.

Thanks,

---

### Post by rampageoberon on 2008-11-18
To correct the .dmrc permissions do CTRL+ALT+F1 and login as your user and run this command

```
chmod 644 ~/.dmrc
```

Also check that you own your home directory

```
ls -l /home
```

Hope that helps

---

### Post by Jacdeb6009 on 2008-11-18
Thanks rampageoberon,

After some messing around it seems that the permissions to my home directory got screwed up.

Eventually after a couple of attempts I seem to have gotten them corrected and the system now boots properly.

I am still puzzled as to how this happened since I don't generally mess with file and directory permissions, but there you go... :)

---

### Post by rampageoberon on 2008-11-18
Well done, at least you got it fixed.

These things can happen from time to time even though we try to be careful.

---

