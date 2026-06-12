---
title: "password problem"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by craftyuk on 2008-11-10
i am new to ubuntu.  a friend installed it for me and i am having problems with installing java.  any which way i try to install i am asked for passwords and i have not set any.  are there standard ones set?  how do i find out.

all help gratefully received.


craftyuk

---

### Post by MasterSander on 2008-11-10
it should be the password you gave at install, call your friend for the password :D

---

### Post by Keen101 on 2008-11-10
Well, your friend had to set up at least **one** password for ubuntu when he was installing....  So ask your friend what he set your password to.

---

### Post by metallicamike on 2008-11-10
well,another thing you can do is go into recovery mode in the session part of the login screen, the select root, then selec who u want to log in as and from there it should sa [email]root@.........blah[/email] stuff, then type "passwd" command annd it will ask you what you want your new password to be. adnd you should be good :)

---

### Post by bodhi.zazen on 2008-11-10
> **metallicamike said:**
> well,another thing you can do is go into recovery mode in the session part of the login screen, the select root, then selec who u want to log in as and from there it should sa [EMAIL="root@.........blah"]root@.........blah[/EMAIL] stuff, then type "passwd" command annd it will ask you what you want your new password to be. adnd you should be good :)

well not exactly ...

Ubuntu uses sudo, so sudo <command> or for a root terminal use gksu.

So the password is the same as your log in password.

If your user is not in the admin group, you will need to modify that (which we can do from the recovery mode).

---

