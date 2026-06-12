---
title: "Home Directories readable to other users"
date: 2008-05-19
forum: Recurring Discussions
---

### Post by Wederik on 2008-05-19
Under Hardy Heron I have noticed my second 
user can access the directories of my first 
user without me having set a NFS or SAMBA 
Share. I have changed the permissions.

Not a problem for a SoHo user but Admins 
should be aware of it.

Wederik

---

### Post by Nepherte on 2008-05-19
That's one of the first things I always do: ```
chmod 0700 homedirectory
```

---

### Post by sdennie on 2008-05-19
You can also set it so that user home directories are initially created with more strict permissions by editing /etc/adduser.conf and changing DIR_MODE from 0755 to 0700.

---

### Post by jdong on 2008-05-19
Yeah, there's a lot of schools of thought on what mode a home directory should be... Ubuntu does use readable-to-others for everything except the extremely sensitive (i.e. keychains, private keys, etc). A good sysadmin should be checking and reconfiguring such permissions as necessary, and for that matter, a good user should be checking his/herself this too.


With that said, IMO there should be a GUI way of choosing default home directory permissions when creating a user, such as what Windows XP's add user tool lets you do.

---

