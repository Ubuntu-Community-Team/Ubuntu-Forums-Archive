---
title: "get rid of keyring"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by trav9595 on 2014-07-10
my keyring prompt keeps popping up all over the place... how do I reset it to default off.??

---

### Post by mooreted on 2014-07-10
Found this:

[http://binaryimpulse.com/2013/06/safely-removing-gnome-keyring-from-xubuntu-12-04/](http://binaryimpulse.com/2013/06/safely-removing-gnome-keyring-from-xubuntu-12-04/)

---

### Post by coldcritter64 on 2014-07-11
> **mooreted said:**
> Found this:

[http://binaryimpulse.com/2013/06/safely-removing-gnome-keyring-from-xubuntu-12-04/](http://binaryimpulse.com/2013/06/safely-removing-gnome-keyring-from-xubuntu-12-04/)
**Question** @ OP, Have you recently changed your user/sudo password with credentials stored in the gnome keyring at the time of the password change ? That is one possible cause of a user password for login not being in sync with the gnome keyring.

**IF** you have recently changed your user/sudo password, rather than disabling/killing off the whole keyring package redo any credentials stored in the gnome-keyring to the new password, no more prompts. Open "Passwords and Keys" in system settings to access stored log-in credentials and alter them in there.

**If** that still fails, deleting the file /home/<username>/.gnome2/keyrings/login.keyring and resetting the user password from a recovery console (remounting the root partition as read/write may be necessary) will get the keyring and the user password back in sync. Rebooting back to a desktop and redoing any login credentials for your install will stop the prompts. It is not usually needed to remove the gnome-keyring.

Edit: OP which release of xubuntu are you using ? The location for the login.keyring may vary in newer releases.

---

