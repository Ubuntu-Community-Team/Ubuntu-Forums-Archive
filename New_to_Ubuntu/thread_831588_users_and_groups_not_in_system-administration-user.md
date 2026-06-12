---
title: "users and groups not in system-administration-users and groups gnome"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by robedeew on 2008-06-17
I just figured out how to access gnome via vnc on the network.  It appears to be unavailable off-site unless I use a vpn client.  The problem I have encountered is that when I want to manage users and groups via gnome, the examples I see say system-administration-users and groups, but users and groups does not appear under system-administration.  

Dapper.  X 6.06

Not sure how to solve this problem. Suggestions?

Will

---

### Post by Corrupt3d on 2008-06-17
Hi,

Sometimes not all the options appear under the menus, however you can easily add them in yourself.

Try doing:

System>Preferences>Main Menu

in the boxes you see try checking off the options that you want displayed.
If its not in there, you can use the 'New Item' button, in command simply type in: *users-admin*

or you can skip all that and just open you a terminal (System>Apps>terminal) and type in:

$ *gksudo users-admin*

---

