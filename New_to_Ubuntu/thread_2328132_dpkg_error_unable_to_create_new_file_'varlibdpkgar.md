---
title: "dpkg: error: unable to create new file '/var/lib/dpkg/arch-new': Permission denied"
date: 2016-06-17
forum: New to Ubuntu
---

### Post by bsrevanth2011 on 2016-06-17
i was trying to install cisco packet tracer.
after downloading the package i extracted it and tried to install it using ./install and i got the following error.

```
Installing 32 bit libraries for Packet Tracer.
dpkg: error: unable to create new file '/var/lib/dpkg/arch-new': Permission denied
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

what am i supposed to do?

---

### Post by &amp;KyT$0P# on 2016-06-17
Try instead
```
sudo ./install
```

---

### Post by cariboo on 2016-06-17
Did you try removing the lock file?

```
sudo rm /var/lib/dpkg/lock
```

---

