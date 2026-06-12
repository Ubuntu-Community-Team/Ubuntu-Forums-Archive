---
title: "Lowering desktop secruity"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Qwertinsky on 2008-08-10
I am getting tired of always having to enter my password just to change seemingly the simplest of settings. 

How can I take Ubuntu (8.04) out of user lock down mode?

---

### Post by Locutus_of_Borg on 2008-08-10
```
sudo -i
visudo

```
look for these lines:
```
# Uncomment to allow people in group wheel to run all commands
%wheel  ALL=(ALL)       ALL

# Same thing without a password
# %wheel        ALL=(ALL)       NOPASSWD: ALL

```
make sure both lines starting with %wheel do not have a # before them

save the file 

make sure you are in the wheel group

ta da

---

### Post by sdennie on 2008-08-10
You can do the above but, my advice would be to just bear with it.  The Ubuntu security model may seem a bit cumbersome at first but, really, once the machine is configured, you'll find that you very rarely need to enter the password because you are rarely doing administrator level tasks.

---

### Post by Qwertinsky on 2008-08-10
> **vor said:**
> You can do the above but, my advice would be to just bear with it.  The Ubuntu security model may seem a bit cumbersome at first but, really, once the machine is configured, you'll find that you very rarely need to enter the password because you are rarely doing administrator level tasks.

I understand this but it is a real P.I.A. when trying to troubleshoot something. 

Also It seems like I always have to enter my password for what I think are simple things like connecting to a WiFi hot spot.

---

### Post by hyper_ch on 2008-08-10
I just wonder what you do when you have to enter the password all the time...

---

### Post by dethredic on 2008-08-12
nvm

---

### Post by nicedude on 2008-08-12
Running wide open is not a very good idea since that defeats allot of the built in security for the system as I understand it and would let anyone walk up to your PC and "rm -r /" or something similar and no more system. But hey its your system so have at it, just thought I would warn you.

---

### Post by billgoldberg on 2008-08-12
Removing desktop security (aka running as root) is a sure way to brick your system.

To my knowlegde you only need to enter your password to install software or edit some system settings, root files.

---

