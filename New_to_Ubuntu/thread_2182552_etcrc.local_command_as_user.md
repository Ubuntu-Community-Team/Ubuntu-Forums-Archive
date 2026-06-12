---
title: "/etc/rc.local command as user"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by after2 on 2013-10-21
Hi guys, i have a little problem with /etc/rc.local so:
I want to start my game server on boot with nice -20 but as user not as root.
I modified "/etc/security/limits.conf" and add  "user -       nice -20".
The problem is when the sistem boot up, the command (sudo -u user nice -n -20 command) start as user but with no nice -20 and i don't get it why. But here is the tricky, if i start manually in terminal /etc/rc.local it starts as user with nice -20. I want to start at boot with nice -20. TNX!

---

### Post by TheFu on 2013-10-21
rc.local is run as root.  To run any specific process as a different user from that script, you must change the user.
I think
**/bin/su {user} command**
is the format.  Don't expect any environment variables to be set automatically. If you want them, then you must set them. Also, always specify the full, complete path to any program you run from scripts.  Definitely check the command above against the man page **before** you run it. That would be "man su"

sudo is for when you are NOT root and want to run as root or some other command. When you already are root, use "su".

---

