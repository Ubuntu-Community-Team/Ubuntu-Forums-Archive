---
title: "Administrative Password?  I Thought I was the Adminstrator"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-06-22
So this is a new one for me.  I'm trying to run a command: [COLOR=#008080]*gksu gedit /etc/default/grub, *[/COLOR]which I've done on previous installs, and it never ask me for an adminstrative password.  I enter my log on password, but that is incorrect.  Also, when I go to User Accounts, I am the adminstrator.  
So what is the adminstrator password for MY machine?  I never entered another password somewhere for admin rights.
Ubuntu 13.04
Thanks for the help

---

### Post by deadflowr on 2013-06-22
See if this works
Open a terminal and type
```
gksu-properties
```
And make sure sudo is the selection.

I read about similar behavior on raring.

---

### Post by GUZZLR on 2013-06-22
Well that was easy...problem solved!  Mine said SU, so I changed it to Sudo, and also changed "screen grabbing" to force enable...dont know if I should have dont that.  At any rate, thanks for getting back so quickly as I was about ready to reinstall.
Thanks for the help

---

