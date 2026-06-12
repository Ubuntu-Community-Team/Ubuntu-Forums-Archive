---
title: "Cannot Login - Username/Password???"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by flezzey on 2008-11-07
Hi, am brand new to Ubuntu - just installed 8.10 tonight but cannot Login - Am hit with Login Screen asking Usernam and Password that I do not posess, nor can find help- anywhere in documentation.

Can someone point me in the right direction please,

Flez
Port Macquarie, NSW, Australia

---

### Post by flezzey on 2008-11-07
I do not recall the Installation Disk asking me for a username, I certainly did not enter one - however, it did ask me for a password, which I entered - would seem the username is teh issue ?

---

### Post by ajgreeny on 2008-11-07
There is no need to install again.

Use the recovery mode at boot up (the second option in your grub menu) and then in the console that should appear eventually, type ```
ls /home
``` and there should be a single name shown in the output.  This will be the name you chose at install so remember that and then type ```
reboot
``` and the machine will restart, and you can use that username, and the password that I hope you do remember.

---

### Post by redbob on 2008-11-07
Other workaround is to create an sudoer user within recovery mode:

> sudo adduser xxxxx
> sudo adduser xxxxx admin

---

### Post by revanb on 2008-11-07
When you installed, it asked you to type in your name. While you typed your name it automatically entered your username. Which if you entered: Peter Pan as your name, your username would have automatically been peter. You could then have altered your username if you wanted, but sounds to me you didn't. You said you entered your password, so there you go. Remember that your password is case sensitive which means   NeverLAND  is not the same as neverland for instance.

---

