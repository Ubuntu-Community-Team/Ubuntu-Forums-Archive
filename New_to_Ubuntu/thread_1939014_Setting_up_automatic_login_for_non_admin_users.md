---
title: "Setting up automatic login for non admin users"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by HomesteadMommy on 2012-03-10
Ok I'm setting up user accounts for my kids one the pc.  I'm trying to set it up so it logs them in automatically. For some reason the option to check not to ask for a password is greyed out in the user settings.  I did find this [info here]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM").
But if I log into my kids account to edit the file they don't have permissions.  That's a good thing. lol  But how do I change to my user name in THEIR terminal to change the file?
Or is there an easier way that I'm not seeing?

Thanks!

---

### Post by fractalman on 2012-03-10
I don't know the correct answer to your problem but i have a suggestion that might work

you could give your kids profile root priviliges, then log into the account and see if you can change stuff that way, then afterwards revoke the root priviliges on the kids account.   

try and see, if not i'm sure someone will have a solution soon :-)

---

### Post by voitrix on 2012-03-11
You can use the [su]("http://manpages.ubuntu.com/manpages/jaunty/man1/su.1.html") command to change user or to gain superuser privileges.

---

### Post by HomesteadMommy on 2012-03-12
Thank you both!  This looks exactly what I was looking for.

---

