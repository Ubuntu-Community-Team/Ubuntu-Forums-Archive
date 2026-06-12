---
title: "Problem loading ubuntu 7.10 (read-only problems)"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by ebony_rogue on 2008-10-18
I have had my ubuntu (dual booting with XP) for a couple months now, but when i started my machine after selecting ubuntu from the grub screen, as it starts to load i get a black screen with the following:

"exec: 7: /etc/init.d/rcS: Input/Output error
init: rcS main process (2433) terminated with status 2
*Loading ACPI modules...                   [OK]
*Starting ACPI services...
acpid: can't open socket /var/run/acpid.socket: Read only file system 
*Starting system log daemon...
chown: changing ownership of '/var/log/mail.warn': Read only file system
chown: changing ownership of '/var/log/user.log': Read only file system
chown: changing ownership of '/var/log/daemon.log': Read only file system
chown: changing ownership of '/var/log/messages': Read only file system
chown: changing ownership of '/var/log/debug': Read only file system
chown: changing ownership of '/var/log/auth.log': Read only file system
chown: changing ownership of '/var/log/mail.err': Read only file system
chown: changing ownership of '/var/log/syslog': Read only file system
chown: changing ownership of '/var/log/mail.log': Read only file system
chown: changing ownership of '/var/log/kern.log': Read only file system
chown: changing ownership of '/var/log/lpr.log': Read only file system
chown: changing ownership of '/var/log/mail.info': Read only file system"

I have really enjoyed using ubuntu and would love to get it back.
Any assistance will be appreciated. I would hate to reinstall ubuntu for the 3rd time...thanks

---

### Post by kilroy423 on 2008-10-19
Usually when I see these errors it is a failing harddrive.  I would boot up to a live cd and then run a smarttest on your drive ```
smartctl -a /dev/YOURHDD
```  pending and reallocated sectors would be what you want to look for.  You could also try an fsck.

---

