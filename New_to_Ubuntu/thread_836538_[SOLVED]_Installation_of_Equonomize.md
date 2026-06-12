---
title: "[SOLVED] Installation of Equonomize"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Felicity_X on 2008-06-21
I attempted to install Eqonomize using Add/Install.  I got the message: "dpkg --configure -a" had to be run in the command line.  I went to the command line and attempted to run it, whereupon I got the message that the command could only be run by a "superuser".  Having ascertained that this is a root user, I went into the user/group preference option and put a password on root user and allocated it the administer system privelege.  I tried to change user at the exit menu and was told that the root user could not sign on at that point.  ](*,)

Can the root user sign in at all?  If so where?  Will it solve the problem I have with Equonomize?

---

### Post by kk0sse54 on 2008-06-21
In the terminal when you need to do something that requires root access you type ```
sudo
``` followed by whatever ever else you were going to type
You don't want to ever log in as root because you can potentially damage your system so sudo gives you temporary root access

---

### Post by Felicity_X on 2008-06-21
Thank you C!oud.  I think my problems with this program have been caused by my pulling the power plug when an attempted installation of P2P Accounts stalled while loading dependencies and I could not work out how to get out of the process or power the system down properly.  I have had proper advice on how to prevent that kind of problem in future, but having run some sudo commands the console had asked me for, it then told me my ubuntu desktop is broken and to reinstall it.

---

### Post by kk0sse54 on 2008-06-21
When your desktop freezes and you can't properly shut it down press control +alt + backspace to restart X which will put you back into the login screen.
You probably lost some data by pulling the power cord so if you have to reinstall it then just pop in a liveCD mount your partition save the data on another partition or external HD then unmount the partition again and reinstall ubuntu.

---

