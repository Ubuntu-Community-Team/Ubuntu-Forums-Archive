---
title: "Error message after toying with Users and Groups"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2012-01-04
I was playing around with permissions and groups in the "Users and Groups" applet in "System -> Administration"

I think I enabled some permissions for myself that maybe I shouldn't have.

When I rebooted my computer I got an error message that said:

"Could not update ICEauthority file /home/user/.ICEauthority"

It was a grey box with a black background that came up before the GNOME desktop.  All it had was a that message and a "close" button at the bottom.
After that the system booted ok, but it is always there when I boot now.

Thing is I can't remember exactly what I did exactly when playing with the permissions.  Is there anything I can do?

---

### Post by wildmanne39 on 2012-01-04
Hi, give this link a look 
[http://ubuntuforums.org/showthread.php?t=1841457&page=3](http://ubuntuforums.org/showthread.php?t=1841457&page=3)
Post 28
thanks

---

### Post by Basher101 on 2012-01-04
sureley one of the ways to learn linux is to break it and fix it again...not something i prefer to do but everyone his/her own..

---

### Post by Learning Linux 2011 on 2012-01-05
Thanks wildmanne, post #29 worked for me.  

There was a hidden .ICEauthority file in my home directory that was locked.  It only had root access, so I changed the permissions so that I (the user) had read and write permission.

---

### Post by wildmanne39 on 2012-01-05
Hi, your welcome! I am glad you got it working.
Thanks

---

