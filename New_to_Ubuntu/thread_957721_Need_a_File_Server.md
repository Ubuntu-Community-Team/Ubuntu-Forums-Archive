---
title: "Need a File Server"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Zeph79 on 2008-10-24
Hey everyone, my needs have changed a bit and I am needing a generic file server for about 50 computers.

Nothing fancy but each department will have to have their own folder where the other departments cant access.   The workstations are windows xp.

I tried downloading the server version of ubuntu but I cant seem to find a GUI or web interface to configure it so I am now looking at the desktop version.

I just need to make a dozen folders, give them permissions, and them map the workstations running XP to those shares.

Can the desktop version handle that?

---

### Post by bjornie on 2008-10-24
Yeah, sure it can. Use synaptics (System > Administration > Synaptic Package Manager) to uninstall/remove software you don't have use for on a server.

---

### Post by northern lights on 2008-10-24
The server version installs without a GUI by default. Running ```
sudo apt-get install gnome-desktop
```will make it look and feel just like the desktop edition though.

It's equally possible to make the desktop version behave the way you want.
Install *LAMP* and *samba* for starters.

In either case, create a group for each department, thereupon add the users to the respective groups and lastly set passwords for the users.
This can be done either via "System > Administration > Users and Groups" in the gnome menu or via the```
[groupadd]("http://linux.die.net/man/8/groupadd")
``````
[useradd]("http://linux.die.net/man/8/useradd")
```and```
[passwd]("http://linux.die.net/man/5/passwd")
```commands.

---

