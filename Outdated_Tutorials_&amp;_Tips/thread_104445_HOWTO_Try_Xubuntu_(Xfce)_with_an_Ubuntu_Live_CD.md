---
title: "HOWTO: Try Xubuntu (Xfce) with an Ubuntu Live CD"
date: 2005-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Limulus on 2005-12-16
There aren't [Xubuntu]("https://wiki.ubuntu.com/Xubuntu") Live CDs yet, but if you're curious to test Xfce, here's how you can do it with an Ubuntu Live CD on a relatively recent computer with internet access (I tested this on a P4 with plenty of RAM...  this procedure won't run on an older computer you'd actually want to install Xfce on ;)

First, boot from the Live CD like normal.  When Gnome's all loaded up, open a Terminal window and run:

*sudo gedit /etc/apt/sources.list *

Replace the contents of the file with this:

```
# Official Ubuntu Repositories
deb http://archive.ubuntu.com/ubuntu/ breezy main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-security main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main universe multiverse restricted
```

Then run Synaptic (ignore the error message and press Reload). Mark all the packages that start with *xubuntu* for installation and Apply.  This will take a little while, so in the mean time, create a new user: *System -> Administration -> Users and Groups* (just something simple for you to log in and out with)

When Synaptic is finished, Log Out of Gnome; the login screen will appear.  Press the Sessions button and select the Xfce entry.  Login with the new username and password.

Squeek! ;)

---

### Post by Limulus on 2006-02-05
Instead of creating a new user, you can alternately run "sudo passwd ubuntu" in Terminal (use a simple password like "test") and then when you log back in, login as "ubuntu" (with the password you set).

Edit: Oh and to avoid getting that error message (and needing to press reload) in Synaptic, **before** you close the Terminal window or run Synaptic, run *sudo apt-get update*

---

### Post by madchicken on 2006-02-05
Cool, thank you very much. I'll test it soon.

---

