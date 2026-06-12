---
title: "Linux as emulated terminal?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by trachean on 2008-06-26
I'm needing to use a Linux machine as a terminal of a Unix machine, as a method of cutting costs. I'm assuming I'll need a terminal-emulator program, and a guide to the terminal-setup process is going to be a must. Can somebody point me in the right direction? 

Thanks!

---

### Post by Rocket2DMn on 2008-06-26
You can use SSH to connect to the Unix machine, or remote desktop like VNC to have a GUI interface to the UNIX server.  You can also mount your home directory on the UNIX machine onto the linux machine using SSH/SFTP.  Otherwise you would need to install Unix (like SunOS Solaris) on the machine to act as a client to the server.

---

### Post by Ducatiboy Stu on 2008-06-26
Putty is available

or Gtkterminal which is similar to Hyperterm

---

