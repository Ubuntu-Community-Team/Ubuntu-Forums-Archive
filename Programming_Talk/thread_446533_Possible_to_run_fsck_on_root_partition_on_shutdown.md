---
title: "Possible to run fsck on root partition on shutdown?"
date: 2007-05-17
forum: Programming Talk
---

### Post by musther on 2007-05-17
I've developed a tool for running fsck when it's due without bugging the user.  At present, in order to run it on shutdown, it actually shuts down the machine, restarts it, runs fsck and then shuts down and powers off.

So, I'm wondering if it is possible to run fsck on all drives after they're unmounted as the system shuts down?

My tool is at:
[http://wiki.ubuntu.com/AutoFsck](http://wiki.ubuntu.com/AutoFsck)

Thanks

---

### Post by FuturePast on 2007-05-17
The shutdown scripts are in /etc/init.d and for each runlevel in /etc/rc* .
You can do with those what you want.

Look up sysv-rc.

---

### Post by Ramses de Norre on 2007-05-17
Make sure to unmount the disk first, you'll run into serious damage otherwise.

---

