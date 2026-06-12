---
title: "[SOLVED] Hibernate and Suspend fail in Hardy on HP Desktop"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Michl on 2008-09-02
Installed Heron on an HP dc7800 and everything seems fine
except hibernate and suspend.  With Hibernate, the computer
turns off correctly and then automatically restarts into
the hibernate login screen as if it was turned on.

With suspend it turns off and nothing brings it to life
except a forced reboot.

Thanks

---

### Post by appier on 2008-09-02
I have run into the same problem with a Compaq SR1717.  Strangely enough, the same computer also does the same thing in Windows XP.  If it goes into hibernate the hard drive can whir for up to ten minutes before it give me access to the system again in XP.  My solution is to just never allow it to hibernate, but that is not really a solution...

---

### Post by Michl on 2008-09-04
Thanks -- that helps.  So it isn't a ubuntu problem
Michael

---

### Post by ozzyprv on 2008-09-04
Yuo may find a solution in this post (or attahced document)

[http://ubuntuforums.org/showthread.php?t=793553](http://ubuntuforums.org/showthread.php?t=793553)

---

### Post by biggest lund on 2008-09-04
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by Michl on 2008-09-04
Solution for Hibernate (Suspend to Disk):  in Bios setup disable LAN wakeup.

Suspend (to RAM) still does not work on this Desktop.

---

