---
title: "bug in linux-libc-dev?"
date: 2007-06-03
forum: Programming Talk
---

### Post by orrorin on 2007-06-03
Synaptics update manager shows that there is an update available for linux-libc-dev. However, it also says that there is a pending bug against it. ...

grave bugs of linux-libc-dev (2.6.20-15.27 -> 2.6.20-16.28 ) <done>
#425595 - gcj-4.1: FTBFS: ../../../src/boehm-gc/os_dep.c:21:28: error: operator '<=' has no left operand (Fixed: linux-2.6/2.6.21-3)
Merged with: 423462
Summary:
linux-libc-dev (1 bug)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]

What should I do? update? wait for fix? If it is not spurious, it does look serious enough to break a compile. Has anyone run into problems with this update??

Thanks.

---

### Post by nealmcb on 2007-12-23
Yeah - this is confusing.  It turns out to come from apt-listbugs as
discussed here:
 [http://ubuntuforums.org/showthread.php?t=531951](http://ubuntuforums.org/showthread.php?t=531951)

and I doubt that going ahead with the install would hurt anything.

---

### Post by Majorix on 2007-12-24
Actually many many programs include non-listed/non-fixed bugs. But you are using them, without knowing they do.

It is safe to install it, as long as you won't feel bad, but then you shouldn't.

---

### Post by nealmcb on 2007-12-24
When I ran into this message, I was doing an apt-get upgrade on a stable system (gutsy).  I would think it would be relatively rare for an upgrade to not be the right thing to do, although of course such circumstances exist.

But what puzzled me the most is that it was a debian bug that was reported:

serious bugs of linux-libc-dev (2.6.22-14.46 -> 2.6.22-14.47) <pending>
 #435700 - keepalived: FTBFS: conflicting types for 'loff_t'
   Merged with: 434040
 #429064 - linux-libc-dev: <linux/types.h> conflicts with <sys/ustat.h>

and according to the man page, debian is what apt-listbugs checks against.

That prompts me to wonder if I really do want apt-listbugs - how often are debian bugs relevant to ubuntu upgrades?  And does anyone know more about this particular upgrade?  And is there a similar package to check for launchpad bugs?

---

