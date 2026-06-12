---
title: "[SOLVED] Virtualbox - can't get it to work?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by socngill on 2008-06-14
I have installed Virtualbox and gone through the set-up procedure to add WinXP, however when I go to start it so I can install the OS I get this message:


[COLOR="Red"]The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}[/COLOR]

Maybe I am being dumb, but I am the only user on this machine, so how could I not have access to it?  Seems bizarre.  How do I go about making the necessary changes in order to get this to work?

Thanks.

---

### Post by sam_delta on 2008-06-14
go into system>admin>users and groups, then click unlock, type your password, then manage groups, then select the group vbboxuser, propertied, and select your user name

you will need to log out and then log in again 
sam

---

### Post by benste on 2008-06-14
Or maybe you didn't install the guest module of Vbox (which i did)
you restart after installation
and be in the mentioned group

---

### Post by vinceUUUU on 2008-06-14
Hello

The second reply to this thread looks similare to something that worked out nicely for this same problem with me.

Settings...users....group...

error messages often are only an indication that the user of the computer knows about...the error message won't necessarily be directly affiliated to anything that a beginner or lighter weight computer user would get the benefit from...

This is indeed, WHY forums like this exist.

right on!

Vince.

---

### Post by socngill on 2008-06-14
> **sam_delta said:**
> go into system>admin>users and groups, then click unlock, type your password, then manage groups, then select the group vbboxuser, propertied, and select your user name

you will need to log out and then log in again 
sam

Thanks Sam, that's done the trick!

This communities great!

---

### Post by sam_delta on 2008-06-14
no problem, glad it work

enjoy ubuntu :)
sam

---

