---
title: "Create new user group with certain rights"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by Azrael84 on 2012-10-06
Hi,

I would like to create a new user group that can: mount second hard-drive, perform dejavu backup and access a truecrypt volume . At the moment these things can only be done by the admin, but I need to allow another non-admin user to do these things.

I think I must create a new group and endow it with these rights, then add the user to that group. Not quite sure how to do all that though.

thanks for any help

---

### Post by Azrael84 on 2012-10-07
I did what I wanted in the end by created by managing groups with the info at [http://maketecheasier.com/add-remove-user-to-groups-in-ubuntu/2012/07/30](http://maketecheasier.com/add-remove-user-to-groups-in-ubuntu/2012/07/30) and then creating a truecrypt group. Before adding

# Users in the truecrypt group are allowed to run TrueCrypt as root. %truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
to visudoers

---

