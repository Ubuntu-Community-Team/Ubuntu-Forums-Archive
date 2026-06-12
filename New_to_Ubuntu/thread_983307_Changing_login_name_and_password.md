---
title: "Changing login name and password"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-11-15
Is there a way to change your login name and password.  I setup a computer for my wife and now she does not like it and wants a different name and password.  Any help would be appreciated.

---

### Post by Tamlynmac on 2008-11-15
system/administration/User & Groups
Select user name and left click on properties
At bottom of Account Tab - Change password (twice) one is a confirmation.

---

### Post by fiddler616 on 2008-11-15
Don't quote me, but I'm pretty sure you can't change the username.
As a workaround, you could create a new user with the desired username, and then just copy [s]the /home folder.[/s]Edit: copy necessary files

---

### Post by jenkinbr on 2008-11-15
> **fiddler616 said:**
> Don't quote me, but I'm pretty sure you can't change the username.
As a workaround, you could create a new user with the desired username, and then just copy the /home folder.
I would do this except for copying the home folder - just copy the needed files into a new home folder for the new user.  I believe there are many hidden files that are tied to that user, and could cause problems if the whole folder is simply copied.

---

### Post by fiddler616 on 2008-11-15
> **jenkinbr said:**
> I would do this except for copying the home folder - just copy the needed files into a new home folder for the new user.  I believe there are many hidden files that are tied to that user, and could cause problems if the whole folder is simply copied.
Good call, I edited the original post, to avoid confusion.

---

### Post by Iowan on 2008-11-15
It can be done, but it's ugly.  You can manually edit /etc/passwd and /etc/shadow, and change directory (and ownership) in /home. Then change the password via **passwd** command.  Oh, you'll probably need to edit new user into admin group.
It's probably easier to add another user/password, then copy what you want from the old user.(The  new user will need to be added to admin group - unless you don't want her as admin.)

---

