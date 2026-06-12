---
title: "[SOLVED] Your user name is unknown to Sudo!"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by JohnDorian on 2008-07-31
I just created a new user account, set permissions to enable this user to administer the system. Using this new account, whenever I try to do something that requires a sudo password I get a window stating "Your user name is unknown to Sudo!"

Ideas?
thanks!

---

### Post by tuxxy on 2008-07-31
check your users and groups and see if the permissions are infact set

---

### Post by aysiu on 2008-07-31
Try this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by JohnDorian on 2008-07-31
Thanks for the lightning fast responses!  I figured I'd be waiting for a while.  I found a solution that worked lighting fast.  Not sure if this is a bug in the gui.  I checked group membership via System Settings>User Mgmt and it was listed as being in the admin group.  I was going to reboot and see but that is 1 of the things about Windows that drove me to linux...

The below worked like a charm.

[http://ubuntuforums.org/showthread.php?t=818713&highlight=user+unknown+sudo](http://ubuntuforums.org/showthread.php?t=818713&highlight=user+unknown+sudo)

> **Oldsoldier2003 said:**
> run the command ```
id <your user name>
``` and if you are not part of the group "admin" run ```
usermod -aG admin <your_user_name>
``` as root

> **vor said:**
> It sounds like the user you are logged in as isn't in the admin group.  If you are able to get to root in some manner, this should fix it:

```

adduser your_username admin

```

---

