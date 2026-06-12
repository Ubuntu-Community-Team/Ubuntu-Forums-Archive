---
title: "Authenticate requests - ubuntu-13.04-desktop-i386"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by lardarzz on 2013-07-31
i have just done a clean install of ubuntu-13.04-desktop-i386 on my laptop to try it out i have no knowledge of the system 

the problem is when i go to the software centre and try to download anything or if i try to unlock my profile on accounts section i keep getting a box popping up saying 
" Authentication is required to change user data" it has a box to insert a password i have tried the passwords i have used on ubuntu but it keeps coming back as failed.
when i installed on laptop it asked me to create a key ring password which i did but tried that also with no joy and have no idea what the keyring password is actually for

---

### Post by Vladlenin5000 on 2013-07-31
Authentication is always required for such operations. Now, the authentication required is your user password, the same you use to start the session. If you have selected automatic login then you might have to unlock the keyring using its own password previously defined by you before doing such operations and even before connecting to a WiFi network.

---

### Post by lardarzz on 2013-07-31
thank you very much i am now up and running

---

### Post by Vladlenin5000 on 2013-07-31
You're welcome.

Please note: AFAIK Ubuntu is the only distro where the first user of a given installed system is also automatically "administrator" (i.e. root). As such the root password required = first user's password. Other distros, including Debian - Ubuntu is Debian based -, during install asks for a root password to be defined regardless of the user or users added during or after the installation. Therefore, in the same situations where Ubuntu requires authentication, in other distros that means the root password defined during the installation.

---

