---
title: "More of a why than a how (about rebooting)"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by 3Nex on 2013-04-02
I'm just wondering why is it neccessary, in every linux environment i've worked on so far, to enter the root password when rebooting through terminal, when there's a working reboot option in the actual desktop environment anyway, which doesn't require the password? I do understand this means that this approach only works if you have a desktop environment installed and that it's not possible to reboot command-line-only linuxes without root access, i just don't understand the philosophy behind it. 

(same goes for shutdown)

---

### Post by Cheesemill on 2013-04-02
I think it's mainly historical, UNIX (and Linux) were designed as multi-user systems where 10's or even 100's of users are logged on and working at any one time.

Imagine what a mess it would be if just anyone could shutdown and reboot without having the proper credentials. :)

---

### Post by grahammechanical on 2013-04-02
As an experiment, try setting up another user on your machine. Give that additional user Standard privileges. Then try shutdown/restart from that user account. If the additional user is not the first or only user you may find that you only get as far as login. To put it another way, we have to switch users to the user with Administrative privileges in order to shutdown unless that additional user was the first user to login.

Regards.

---

