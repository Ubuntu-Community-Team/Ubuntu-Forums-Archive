---
title: "Problem disabling Keyring"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by thomsany on 2008-08-21
Hey guys, I followed the following instructions to bypass the keyring prompt everytime I start Ubuntu:

Install libpam-keyring and add to the end of /etc/pam.d/gdm:

@include common-pamkeyring


For some reason the prompt keeps popping up everytime I restart as if I hadn't done anything.
The passwords are the same for login and keyring so there shouldn't be an issue.

Please help.

Regards,

Teo

---

### Post by forger on 2008-08-21
Not sure about this one, I can just help you check if it's installed:
```
apt-cache policy libpam-gnome-keyring
```

You could however reinstall it:
```
sudo apt-get install --reinstall libpam-gnome-keyring gnome-keyring libpam0g
```
reboot your machine and see if it's fixed

found some info: [http://live.gnome.org/GnomeKeyring/Pam](http://live.gnome.org/GnomeKeyring/Pam)

---

