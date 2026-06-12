---
title: "Unable to shutdown,. Restart OK"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by odror on 2011-10-11
OS: ubuntu 11.10 

When I try to shutdown my computer hangs on the ubuntu screen. I can restart with no problem.

I switched to VT mode and stopped gdm/lightdm.

then when root type "shutdown -h now"

I get multiple error similar to the following:

S90halt: Permission Denied. 

The computer hangs after the S90halt error.

I do not get the permission denied errors with "shutdown -r now"

Where can I fix these permission?

Thanks

---

### Post by collisionystm on 2011-10-11
Reboot is 
 
sudo shutdown -r 0
 
Shutdown is
 
sudo shutdown -P 0

---

### Post by odror on 2011-10-11
> **collisionystm said:**
> Reboot is 
 
sudo shutdown -r 0
 
Shutdown is
 
sudo shutdown -P 0

Both commands are equivalent. I get the same hangout if I use the menu to reboot. I do not think that the issue is the command line. the issue is the fact the "root" is not permitted to shutdown.

---

### Post by jerrylamos on 2011-10-12
My experience, on a new development, the LAST things to work are Grub, Install, and Shutdown.  Apparently these have low priority with development.

I frequently do from a terminal session "sudo shutdown now" and also "sudo restart" which sometimes works.  When all hard drive activity has ceased for 20 seconds I hit the power off button.

Today, Install got an "error" when putting grub on /dev/sda.  Bug #872845.  Took me several hours to finally get going....I thought I'd lost the hard drive altogether.

Jerry

---

### Post by odror on 2011-10-12
The problem is now solved. For some reason in the directory /etc/rc0.d the file S90halt (and others) where not a symbolic link to ../init.d/halt. It was a regular file with No exec permission. Because of that halt was not executed and the system did not shutdown. That is why I got these permission errors.

---

