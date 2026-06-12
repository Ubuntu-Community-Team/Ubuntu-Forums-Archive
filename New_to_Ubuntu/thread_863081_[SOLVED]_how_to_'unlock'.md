---
title: "[SOLVED] how to 'unlock'?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by candtalan on 2008-07-18
I administer a machine for a club and they use it on a second user account not the admin (first user) account. 

I can log into the admin first user account ok but when I go to log into their account it looks as if it has been locked. I get a display asking for password? and options for 
Leave Message
Switch User
Cancel
Unlock

What has happened please?
As Admin I now need to revert to normal operation, and passwords are in my control, so I would be grateful for advice about  unlocking and also to avoid it happening again?

tia

---

### Post by hyper_ch on 2008-07-18
I'm not really getting what the problem is. Can you describe it in more details?

---

### Post by schauerlich on 2008-07-18
> **candtalan said:**
> I administer a machine for a club and they use it on a second user account not the admin (first user) account. 

I can log into the admin first user account ok but when I go to log into their account it looks as if it has been locked. I get a display asking for password? and options for 
Leave Message
Switch User
Cancel
Unlock

What has happened please?
As Admin I now need to revert to normal operation, and passwords are in my control, so I would be grateful for advice about  unlocking and also to avoid it happening again?

tia

I'm not sure I understand your situation. In order to switch to another user, you need to know the user's password.

---

### Post by Lod on 2008-07-18
It's probably the screensaver. After 10 minutes it starts and I believe the default behaviour is that it also locks your session.

Change this, if needed, in System - settings - Screensaver (not sure about the path, I'm not on linux at the moment).

---

### Post by candtalan on 2008-07-18
Thanks.

It is my (volunteer) job. I control the machine, I set the passwords, I know what the user password is (or should be).

When I log into the first user account all is ok. this is the account with sudo rights.

when I try to log into the account for the second user (no sudo rights), I am faced with the locked screen (see above) and it does not seem to accept any known password.

It looks as if a session (?) has been locked(?) I need to know what has happened, how can it have been locked, and what I can now do to unlock it (?) and hopefully how to avoid it in the future.
Is that any help?

---

### Post by hyper_ch on 2008-07-18
reset then the password of that user account

```

sudo passwd USERNAME

```

and enter a new one (or the same again)

---

### Post by candtalan on 2008-07-18
> **Lod said:**
> It's probably the screensaver. After 10 minutes it starts and I believe the default behaviour is that it also locks your session.

Change this, if needed, in System - settings - Screensaver (not sure about the path, I'm not on linux at the moment).

in this case, how do I do this for second user, while I am logged in as first user?

---

### Post by Lod on 2008-07-18
I've no idea. It's probably somewhere in the .gnome2 directory of that user.

---

### Post by candtalan on 2008-07-18
sudo passwd USERNAME

this did the trick. Thanks so much for your responses!

---

### Post by hyper_ch on 2008-07-18
then you can mark this thread as "solved" by using the "thread tools" on top

---

