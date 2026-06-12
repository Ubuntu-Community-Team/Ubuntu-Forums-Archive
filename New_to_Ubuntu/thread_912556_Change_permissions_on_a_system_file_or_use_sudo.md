---
title: "Change permissions on a system file or use sudo?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Skorzen on 2008-09-05
I have a newbie question:

When someone wants to install a program in Ubuntu without 'sudo' then the output seems to be the following:
```
someone@somewhere:~$ apt-get install <package-name>
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Is it safer to run as 'sudo' or to change /var/lib/dpkg/ permissions?

---

### Post by FuturePilot on 2008-09-05
> **Skorzen said:**
> I have a newbie question:

When someone wants to install a program in Ubuntu without 'sudo' then the output seems to be the following:
```
someone@somewhere:~$ apt-get install <package-name>
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Is it safer to run as 'sudo' or to change /var/lib/dpkg/ permissions?

There's just no way to install something without root privileges into the root file system. You *need* to use sudo to install something with apt.

---

### Post by scorp123 on 2008-09-06
> **Skorzen said:**
> Is it safer to run as 'sudo' or to change /var/lib/dpkg/ permissions? First of all, it's not very wise to change the permissions of *ANY* system file without exactly knowing what it does, why it is needed, and what the consequences are. If a file belongs to "root" (which would be the case here!) then you can assume that it is considered being a more or less essential "system file" and your normal user account is not supposed to touch it or mess with it.

Secondly, even if you used "sudo" (DONT DO IT!!) and changed the permissions of that file, you would not get much further. The installation would still fail because your account would still lack the appropriate write permissions into any of the folders where a program's binaries usually get installed into, e.g. /usr/bin ... That location is off limits for normal users as far as writing is concerned (only "root" can save, remove and overwrite programs there!). Same for the /etc folder where usually all config files are stored. Most programs need to store their system-wide configuration there and that too would fail, so the installation would most likely be aborted.

So the lesson here is: To use the desktop, use progams, surf the web ==> use your normal account.

For installing and removing stuff, reconfiguring the system --and *ONLY* for these type of activities!!-- use "root", e.g. via the "sudo" command.

---

### Post by lazyart on 2008-09-06
> **scorp123 said:**
> So the lesson here is: To use the desktop, use progams, surf the web ==> use your normal account.

For installing and removing stuff, reconfiguring the system --and *ONLY* for these type of activities!!-- use "root", e.g. via the "sudo" command.

+1

This is one reason why Linux is resistant to virii and malware.  By default you do not have the power to mess with system files or install software (which is exactly what insidious software depends on).  Sudo might be a pain, but you get used to it (it's only 5 extra characters).

---

