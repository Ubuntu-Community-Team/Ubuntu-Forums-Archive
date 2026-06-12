---
title: "Server / Ubuntu running Xibo"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by frits_goed on 2013-11-04
hello,

im new at ubuntu. Im running Xibo on a server on ubuntu,

but now i cant change my password because, i dont have a physical connection to the server. Or i have no physical acces.

What i do have is a VNC connection by IP.

My question is as follows,

is there a way for me to change the password of the current logged in user?
When i reboot the ubuntu pc, it automaticly logs in the current account.

Greetings Opperdere.

---

### Post by TheFu on 2013-11-04
No clue what Xibo is .... 

To change your password, open a terminal and type **passwd**. You will need to know the prior password.
No physical access is needed.  If you do not know the old password, then ask the main server administrator to reset your password.

For remote servers, ssh should be the primary mode of remote management. By using ssh-keys, you can remote in from almost any device from anywhere in the world and do everything to manage a server.

---

