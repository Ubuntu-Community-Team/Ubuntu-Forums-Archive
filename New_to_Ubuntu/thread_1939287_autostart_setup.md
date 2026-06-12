---
title: "autostart setup"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-11
I am using kde-desktop in Lucid. Can I enable choice of Gnome or KDE desktops on bootup?
Tried as shown below, & am confused about the  output..
To set kdm restart
bump@bumpyputer:~$ sudo /etc/init.d/kdm restart
[sudo] password for bump: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service kdm restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart kdm
kdm start/running, process 12808
bump@bumpyputer:~$ 
I would appreciate help on this please.

---

### Post by ubudog on 2012-03-11
At start, before logging in, there should be an option at the bottom of the screen.

---

### Post by Bumpalot on 2012-03-11
I cannot restart (which I want to do) - can only logout. 
The KDE desktop is blank, no lower panel or message.
The KDE screen icon appears & the full desktop opens.
This is where I need to be able to choose either Ubuntu or KDE.
Also,2 screen messages appear showing "Session 'default' is already opened in another kate instance, change there instead of reopening?" (due to 2 files left open when I logged out)
How can I change settings so opened files will be restored automatically on log out or reboot.
I have messed up somehow!

---

### Post by Bumpalot on 2012-03-11
Closed this due to lack of response. Gone to KDE Community.

---

