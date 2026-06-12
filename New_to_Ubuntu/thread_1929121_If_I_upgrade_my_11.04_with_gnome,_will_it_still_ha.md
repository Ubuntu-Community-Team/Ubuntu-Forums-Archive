---
title: "If I upgrade my 11.04 with gnome, will it still have gnome ?"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by derek45 on 2012-02-21
I'm running 11.04 with gnome 

If I upgrade to 11.10,  will gnome still be there,  or will I have to re-install it?

Thanks

---

### Post by forrestcupp on 2012-02-21
If you do an upgrade instead of a clean install, everything you already have should be upgraded to the new versions.

Edit: I doubt if you'll still have Gnome2, though. Since 11.10, Ubuntu uses Gnome3.

---

### Post by MARP1961 on 2012-02-21
If you do a fresh install of Ubuntu 11.10, the default desktop environment will be Unity with it's infamous side launcher. If you want Gnome Shell simply install it via the Software Centre or in Terminal:
```
sudo apt-get install gnome-shell
```

Once installed, you have a choice at the Login Screen. Just click the gear icon and select 'Gnome' instead of 'Ubuntu'.

---

### Post by derek45 on 2012-02-21
This would be an upgrade from the currently installed 11.04

Not planning on doing a complete re-installation, unless there is some reason I should do so.

---

### Post by wildmanne39 on 2012-02-21
Hi, well a fresh install with 11.10 would work better most likely, just back up your important data first.

In 11.10 you have to install gnome shell after it is installed so it might create problems already having it installed in 11.04, it would probably have to remove gnome to upgrade to 11.10. 

It is very easy to install gnome shell after 11.10 is installed as mentioned in the previous post.
Thanks

---

### Post by forrestcupp on 2012-02-22
> **derek45 said:**
> This would be an upgrade from the currently installed 11.04

Not planning on doing a complete re-installation, unless there is some reason I should do so.

If you're talking about the old Gnome 2 desktop, then no, you won't still have it. Everything is switched to Gnome 3 in 11.10, and it was still running on Gnome 2 in 11.04. You will see a lot of changes when you upgrade. If you install Gnome Shell, you can have Gnome Classic, which is the closest thing you'll get to the old Gnome 2 desktop.

If you're running Gnome 3 and Gnome Shell from a PPA, then it will probably stay close to the same.

Just be warned that sometimes people who upgrade with a lot of PPAs have problems from an upgrade. If you don't have a separate /home partition, you might want to back up your important files. You'll most likely be ok, but with the switch from Gnome 2 to Gnome 3, it's a pretty big upgrade.

---

### Post by RememberWhenItRained on 2012-02-22
if you do an update, rather than clean install, then yes, you should still have it. Unity is default, but on the login screen just click the gear and select GNOME.

---

