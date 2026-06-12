---
title: "Rooting fail..."
date: 2013-01-30
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-01-30
OK hello everybody, I would like to ask you for help...I am relatively new to Linux so I am having one problem.
Been running on xubuntu 12.04 LTS, using xfce terminal emulator...when I try to set myself root aka trying to do "sudo su" command I keep getting this message: "Cannot execute gnome: No such file or directory" 
Somebody pls explain what the heck is going on here...Thanks in advance

---

### Post by TheFu on 2013-01-30
**sudo -s** is the command you seek.

Sudo does lots and lots of really cool things.  Reading the man page for sudo explains much.

**$ man sudo **
is the way to do that.

---

### Post by LinuxUser666 on 2013-01-30
excellent, thank you,that worked perfectly and yeah I could use more manual reading :D

---

### Post by Alcidious on 2013-01-30
Keep in mind that since you are using Xubuntu Nautilus is not included as a file manager, since you are not using GNOME. You can install Nautilus side by side with Thunar,or even choose between them. 

Don't know that any of that was related to your problem...

---

