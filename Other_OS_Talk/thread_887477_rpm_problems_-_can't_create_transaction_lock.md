---
title: "rpm problems - can't create transaction lock"
date: 2008-08-12
forum: Other OS Talk
---

### Post by RyanJones187 on 2008-08-12
Hi everyone!

I'm trying to follow the Acronis tutorial [here](http://ubuntuforums.org/showthread.php?t=823433) but everytime I try to run |rpm --initdb| I get this:

> ryan@XANA:~$ sudo su
root@XANA:/home/ryan# rpm --initdb
error: can't create transaction lock on /var/lib/rpm/__db.000
root@XANA:/home/ryan# 


Does anyone know how to fix this or if there is something specific I need to do? Help would be appreciated :)

---

### Post by SunnyRabbiera on 2008-08-12
We really dont use RPM's here, instead we use .debs.
If you need to install this package try to find a debian installer or convert it with alien.
Also another part of your issue is that you need sudo to use root access.

---

### Post by Joeb454 on 2008-08-12
Moved to Other OS Talk, as it seems the OP isn't using Ubuntu.

My basis for this is that RPM's are for Red Hat based distro's, not Debian based ;)

---

### Post by ajmorris on 2008-08-12
> **RyanJones187 said:**
> Hi everyone!

I'm trying to follow the Acronis tutorial [here]("http://ubuntuforums.org/showthread.php?t=823433") but everytime I try to run |rpm --initdb| I get this:



Does anyone know how to fix this or if there is something specific I need to do? Help would be appreciated :)

hi there,

What OS are you using?

---

