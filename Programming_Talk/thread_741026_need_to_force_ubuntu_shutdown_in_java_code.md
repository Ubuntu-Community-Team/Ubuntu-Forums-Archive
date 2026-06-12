---
title: "need to force ubuntu shutdown in java code"
date: 2008-03-31
forum: Programming Talk
---

### Post by brdohman on 2008-03-31
I'm needing to shutdown a ubuntu disc after an amount of time through the command line, which is initiated through java code.  

I plan to use

sudo shutdown -h now

but after putting that in it asks for the password.  i'm unsure of how to get around this using the command line through java.

---

### Post by Zugzwang on 2008-03-31
Your program needs to be run by the root user, then it works.

---

### Post by brdohman on 2008-03-31
is it not possible to run it, if the user is not the root user?

I'm trying to limit computer usage through custom software at a internet kiosk.  So I wrote some code to allow logins pending on how much money they paid for a certain time.  ie: if they pay 5 they can get 30 mins worth of computer usage.  The login screen I created allow them to login with a username and password that I give them, that authenticates itself against current users in the system.

---

### Post by heikaman on 2008-03-31
> **brdohman said:**
> is it not possible to run it, if the user is not the root user?

yes it's possible, add the user to /etc/sudoers like this:

# brdohman
brdohman ALL=NOPASSWD: ALL

now when you "sudo anything" it will not ask you for the password.

one last thing, u can only edit the file sudoers using visudo like this:
sudo visudo.

i hope it's useful. :)

---

