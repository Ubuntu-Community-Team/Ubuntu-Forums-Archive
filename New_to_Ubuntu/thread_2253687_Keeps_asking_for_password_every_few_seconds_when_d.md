---
title: "Keeps asking for password every few seconds when downloading"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by kurt11 on 2014-11-21
Hi. I have 14.04 xcfe on a chromebook.
All works ok but using the software center, it pops up asking for my password when trying to download plex. I put my password in, the message goes away then comes back up about 4 seconds later. This repeats about 10 times before it just says it cant install it. 
Whats going on? Thanks

---

### Post by Rex Bouwense on 2014-11-21
Perhaps you are entering the wrong password.  Make sure that your Caps Lock is not on.

---

### Post by grahammechanical on 2014-11-21
Wrong password. Or, the right password but wrong user. Not a user with the authority to authenticate the task. Neither of these might be true in your case.

Regards.

---

### Post by kurt11 on 2014-11-21
password is correct. It also shows the message when i try to use the updater program, cant seem to do anything on it. Used crouton to install

---

### Post by kurt11 on 2014-11-21
It also does it even if i click cancel, it will pop up several times even when cancelling it repeatedly. The same message pops up when trying to use the updater too. I set a root password when installing with crouton which i know is correct. Caps lock isnt on, double checked by typing in the note pad. surprised its so problematic.

---

### Post by bilkay on 2014-11-21
Ubuntu doesn't have a root password. The initial user (installer) is the administrator (sudoer) who can then add other users and give them admistrator privileges. If you are an administrator, you should enter **your** password to install software.

---

### Post by kurt11 on 2014-11-21
I did put MY password in. Deleted it now anyway buggy piece of crap

---

### Post by deadflowr on 2014-11-21
What is crouton?
Explain

---

### Post by QIII on 2014-11-21
Crouton = installation utility for installing Ubuntu on a Chromebook.

It provides a chroot environment.

---

