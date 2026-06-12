---
title: "How to elevate user status?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by paker on 2008-08-15
How can I become the root user?
I need to set up firewall but I dont' have the privilege to do so. "Since you are not a supervisor, you cannot change firewall setting." 
Thanks.

---

### Post by tamoneya on 2008-08-15
use sudo.  Instead of calling <command> call sudo <command>

Then you enter your password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by nicedude on 2008-08-16
you can also use "sudo -i" in a terminal to get a root terminal, but be careful as you could break anything in this mode.

---

### Post by ben2talk on 2009-05-23
Using GUI - to adjust users and groups for example - the software functions, but requires unlocking - There is a 'user' selector above the password selector, allowing me to choose whatever 'sudo'er account I wish to authorise the job.

This is apparently something that Ubuntu should brush up on, and not behave like XP (which failed primarily for ignoring the multi-user and priviledge system).

now in Ubuntu I am finding that many Admin features are easy to get into, but Synaptic must be run from terminal using 'su MYSUDOACCOUNT' and then 'sudo synaptic'.

I should be allowed to launch synaptic first, and then UNLOCK as any sudo'er.

---

### Post by mcduck on 2009-05-23
> **ben2talk said:**
> Using GUI - to adjust users and groups for example - the software functions, but requires unlocking - There is a 'user' selector above the password selector, allowing me to choose whatever 'sudo'er account I wish to authorise the job.

This is apparently something that Ubuntu should brush up on, and not behave like XP (which failed primarily for ignoring the multi-user and priviledge system).

now in Ubuntu I am finding that many Admin features are easy to get into, but Synaptic must be run from terminal using 'su MYSUDOACCOUNT' and then 'sudo synaptic'.

I should be allowed to launch synaptic first, and then UNLOCK as any sudo'er.

Uuntu doesn't ignore multi-user setups or different user privileges in any way. :D Quite the opposite. The thing here is that in Linux it's possible to run programs as many different users at the same time, and Ubuntu uses this to allow certain users to administrate the system without having to interrupt your normal work and log in as different user.

In other words, when you run programs like Synaptic you are not running them as your normal user. You *run* them as root, but you *start* them from normal user account.

If you prefer stricter separation between normal user and administrator you are free to create two different users, one that belongs to admin group and one that doesn't. Or enable root login if you want. It's just that in most cases doing that will not bring any benefits but just makes things more complicated for yourself.

edit: The reason why Synaptic doesn't have such "unlock" button is that non-admin user have absolutely no reason to start the application, there is nothing they can (or even should) do with a package manager.

---

