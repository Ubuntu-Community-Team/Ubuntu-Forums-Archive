---
title: "Add to Linux StartUp"
date: 2009-07-27
forum: Programming Talk
---

### Post by hosseinyounesi on 2009-07-27
Hi everyone,
How can I add a program to Linux Startup? I want this program to be executed as an user logins and be closed as the user logs off? Any script to do this?
I don't want a daemon (it starts in boot process and doesn't terminate at logoff), I need something that shows an splash at login.
I wrote the splash in Qt and now just I have to add it to startup :(

Thanks a lot for your quick answer :)

---

### Post by Michael3477 on 2009-07-27
System > Preferences > Startup 

That might be what you're after

---

### Post by hosseinyounesi on 2009-07-27
Thanks a lot,
But I have to 1) write a program to do that and do that 2) for all users( As EVERY login occurs ). I have to mention that maybe the user is domain user not local.

Thanks again

---

### Post by hosseinyounesi on 2009-07-27
Hi
I found /opt/kde3/share/autostart/ in openSuse and KDE based, 
/etc/xdg/autostart/ & /usr/share/gnome/autostart/ in ubuntu
and GNOME based linux !!!

Is this the best way?!

---

### Post by x22 on 2009-07-27
> program to run at user login

the usual way is, to list it in the user's .bash_profile
or equivalent for other shells

> to exit at logout

.bash_logout

---

