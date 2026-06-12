---
title: "Where is 8.04.1?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-07-05
Hi,

Ubuntu 8.0.4.  I know that 8.04.1 has been available since this past Thursday, as shown in Distrowatch.  However, it's now Saturday and I am still unable to upgrade my Hardy Heron.  Checked Update Manager: still up-to-date.  Sudo aptitude dist-upgrade also yields zero.

What's going on? 

:confused:

---

### Post by avtolle on 2008-07-05
If:

1) You have 8.04 installed; and

2) You have downloaded and installed all updates,

then you are running 8.04.1, and there is nothing else to install.

---

### Post by kostkon on 2008-07-05
> **iClouseau88 said:**
> Hi,

Ubuntu 8.0.4.  I know that 8.04.1 has been available since this past Thursday, as shown in Distrowatch.  However, it's now Saturday and I am still unable to upgrade my Hardy Heron.  Checked Update Manager: still up-to-date.  Sudo aptitude dist-upgrade also yields zero.

What's going on? 

:confused:
It's not an upgrade. If you have your system up-to-date then it means that you are already using 8.04.1. But to be sure, open the terminal and give
```
lsb_release -a
```

---

### Post by drs305 on 2008-07-05
You can check with:
```
lsb_release -a
```

---

### Post by bodhi.zazen on 2008-07-05
Please see this sticky :

[http://ubuntuforums.org/showthread.php?p=5322677](http://ubuntuforums.org/showthread.php?p=5322677)

---

