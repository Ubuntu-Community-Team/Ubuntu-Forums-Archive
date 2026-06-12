---
title: "Can I change the dull, grey login screen at resume from hibernate?"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by n00b@linux on 2013-02-26
I have a Dell Latitude D430 running stock Ubuntu 12.10.
Resume from disk appears to be working but when I do I am greeted with the standard Ubuntu 12.10 background but a dull, grey rectangle of a login screen.
Is there any way I can change this login screen to something more aesthetically pleasing?

---

### Post by PunkLV on 2013-02-26
There should be an option in gconf-editor. Alt+F2 for gconf and do a search for 'background' it used to be called 'login_screen_background' or similar. 
I don't have an ubuntu machine available right now. Sorry.

---

### Post by n00b@linux on 2013-02-27
Thanks for your help, but I could not locate what you described.
I have done some further investigation.
The login screen appears after I resume from hibernate because of the default settings in SystemSettings > Brightness and Lock.
By default the box "Require my password when waking from suspend" is ticked.
If I untick it, I don't get the login screen when I resume from hibernate.

---

### Post by n00b@linux on 2013-02-27
I've searched and Googled but can't find the solution to my problem.
I would like to change the default (gnome-screensaver?) Lock Screen from its boring 'grey box' look.
Is there a config file I need to change or create in Ubuntu 12.10?

---

### Post by nothingspecial on 2013-02-27
Duplicate thread.

---

### Post by Sef on 2013-02-27
> Duplicate thread.

It was a duplicate.

---

