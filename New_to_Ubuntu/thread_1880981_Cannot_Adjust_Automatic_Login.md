---
title: "Cannot Adjust Automatic Login"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by hephaestionaz on 2011-11-14
I had enabled automatic login in All Settings>User Accounts, however when I rebooted I was presented with the log in screen and I had to key in my password. I went back to All Settings>User Accounts and I am unable to change the Automatic login switch. It's grayed out and when I try and click the Unlock button at the top right of the window  nothing happens. It's also sort of grayed out and when I hover the mouse over the lock, it displays this message: "System policy prevents changes. Please contact your system administrator.". 

I don't know what I did to screw this up. Is there a .conf file somewhere I can edit?

11.10

---

### Post by carranty on 2011-11-14
Sounds like you need superuser privileges.  Do you know what the command line equivalent of 'All Settings >> User accounts' is?

If so run try running it from the command line and put

[I]gksu

[/I]in front of the command.

I'm not sure how to launch it with superuser privileges otherwise.

---

### Post by hephaestionaz on 2011-11-14
Not sure :/

---

