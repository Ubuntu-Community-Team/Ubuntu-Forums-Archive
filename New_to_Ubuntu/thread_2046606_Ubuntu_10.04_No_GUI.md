---
title: "Ubuntu 10.04 No GUI"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Mistrblank on 2012-08-23
I've got a system that over the weekend I rebooted and since then it no longer loads a GUI beyond the "ubuntu" splash screen with 5 red dots under it.

The interesting thing  (at least to me) is the system is definitely loading because I can access the system via ssh.  It also appears that X is starting from the gdm logs, and I can export my display to :0 and force start a gnome-session to the local screen that way.   I just currently do not get to the point where the GDM greeter is starting and allowing me to log in at the box.

---

### Post by Bashing-om on 2012-08-23
mistrblank;
 What version of ubuntu are you running?
Can you start up the X session with startx ? 12.04 has a different command like /etc/init.d/lightdm or some such .. I am not sure at all.

Can we not re-install the desktop to resolve?

[INDENT]kindly regarding <==BDQ

[/INDENT]

---

