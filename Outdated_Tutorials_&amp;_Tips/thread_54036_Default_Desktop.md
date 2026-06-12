---
title: "Default Desktop"
date: 2005-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by betamax on 2005-08-03
Hello,

AS part of setting up ububtu as a possible replacement desktop I need to figure out a way of creating default desktop settings which can be set for each user.

Is there a way I can alter the default theme & desktop which Ubuntu uses when a new user is created ?

Thanks for any help.

Darren

---

### Post by lol on 2005-08-03
I am not sure if this can help a little bit [http://www.gnome.org/learn/admin-guide/2.6/](http://www.gnome.org/learn/admin-guide/2.6/)
You will soon discover that setting system wide preferences for gnome is a real pain. Basically, they just reinvented the wonderful M$ registry database...

When you create a new user, files from /etc/skel are also copied in the home directory. For KDE or other window managers, I really don't know how it works.

---

### Post by betamax on 2005-08-04
Thanks I'll have a look into that.

Darren

---

### Post by npaladin2000 on 2005-08-04
[QUOTE=lol]When you create a new user, files from /etc/skel are also copied in the home directory. For KDE or other window managers, I really don't know how it works.[/QUOTE]

Pretty much the same way.  There's a bunch of hidden "dot" directories under each user from which come a lot of the user-specific GNOME settings, from what I understand.   Unfortunately, I'm away from my PC right this second, so I can't double-check it until I get off work.

---

### Post by kiddo on 2005-08-04
what about [Sabayon]("http://gnome.org/projects/sabayon/") guys?

---

### Post by betamax on 2005-08-04
Ummm think I've found myself a semi-solution using the /etc/skel/ folder...
I configured up a user desktop with the specific wallpaper/icons/themes and folders.

I then did "sudo nautilus" and dropped the following folders from the users folder into the /etc/skel/ folder

.gnome
.nautilus
.gedit
.themes
.icons

Its still has a few issues, it takes ages to start the account, and I've just discovered it gives the new user full root access (umm not so good....)

Ahh well onwards.....

---

### Post by betamax on 2005-08-04
Think Ill give Sabayon a look.

Thanks for the link

---

