---
title: "Annoying Pop-up at bootup"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by gkrules on 2008-05-08
Everytime i log in i get this message:
[IMG]http://i203.photobucket.com/albums/aa149/icemandeeran/problem.jpg[/IMG]
it gets really annoying when im trying to do something really fast 
the first and second days i had hardy heron the message never came up
but now it does and its really annoying
what can i do to stop it from happening so often?


oh and by the way it only comes up when i log in...but my hibernate and standby dont work so anytime i wanna get on i hav to log in

---

### Post by aysiu on 2008-05-08
Do you have autologin activated? Or are you logging in manually?

P.S. Nice theme you have there.

---

### Post by gkrules on 2008-05-08
yea autologin is activated
is that it wats causing it?


and the theme is slickness black from gnome-look.org

---

### Post by aysiu on 2008-05-08
> **gkrules said:**
> yea autologin is activated
is that it wats causing it? I think it's a bug in 8.04. If you have autologin on, you'll always be prompted for your keyring password. If someone else knows of a solution to this, I'd love to know.

---

### Post by gkrules on 2008-05-08
oh i see 
ill prolly just disable autologin cuz
it takes like 15sec for it to go from the login screen to the desktop [w/o autologin its less than 3]

---

### Post by crjackson on 2008-05-08
I'm guessing you may have a wireless connection.  Whenever you login, keyring looks for the password you type in the login box so that it too can do it's thing.  However, when you use autologin, no password is typed therefore nothing is passed to the keyring manager.  I wouldn't really consider that a bug, but a feature to bypass the the keyring password whenever autologin is enabled would be nice.

---

### Post by Ted-B on 2008-05-08
I do not understand why there is not automatic login.  If I log in I do not get keyring.  If I do automatic login I get keyring.  It makes sense and calling it a feature sounds like microsoft.  I have hardy heron.  How do I just automatically login and get my wireless connection?

---

### Post by crjackson on 2008-05-08
> **Ted-B said:**
> I do not understand why there is not automatic login.  If I log in I do not get keyring.  If I do automatic login I get keyring.  It makes sense and calling it a feature sounds like microsoft.  I have hardy heron.  How do I just automatically login and get my wireless connection?

I said it would be nice to have a feature to bypass the keyring.

---

