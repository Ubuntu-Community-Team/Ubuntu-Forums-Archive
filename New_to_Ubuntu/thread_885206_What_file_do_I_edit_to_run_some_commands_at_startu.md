---
title: "What file do I edit to run some commands at startup?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by ovimunt on 2008-08-09
Hi, 

I know there's aa **rc.something** file where you can add commands you want to run at startup. Unfortunately I can't remember the exact name or the location of the file. Can anyone help?

Thanks

---

### Post by Diabolis on 2008-08-09
You can add commands to be executed on startup here:
**system / preferences /sessions**

---

### Post by ovimunt on 2008-08-09
Yeah!  I got it, it's **/etc/rc.local**

---

### Post by aloshbennett on 2008-08-10
Changing /etc/rc.local would affect all the users of the machine which doesnt matter if its a single user desktop :)

If you add your script under system/prefs/session, it would run only for ur user account.

I think it adds to .profile file under your home directory.

---

### Post by sdennie on 2008-08-10
Also note that programs that depend on having a DISPLAY variable set will not work from /etc/rc.local.  For minor tweaks, I also recommend using System->Preferences->Session.

---

### Post by Frak on 2008-08-10
Add it to System -> Preferences -> Session, click New -> and add the path to the script. Make sure the script is executable by running

chmod +x <script/path/here>

EDIT
Got beat to it =\

---

