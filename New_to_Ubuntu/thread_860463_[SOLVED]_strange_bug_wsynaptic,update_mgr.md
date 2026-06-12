---
title: "[SOLVED] strange bug w/synaptic,update mgr"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-15
every time i try to update or update the package mgr i get this:
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
is this fixable???

---

### Post by phidia on 2008-07-15
Check your /etc/apt/sources.list and see [this thread]("http://ohioloco.ubuntuforums.org/showthread.php?t=803585").

---

### Post by drs305 on 2008-07-15
Try opening synaptic, settings, repositories, updates and untick the hardy-updates block. Close synaptic and it will update sources.list. Then "sudo apt-get update".

Next, reopen synaptic and retick the Updates > hardy-updates box. Close synaptic again and it should update sources.list. Run "sudo apt-get udpate" again and it may clear your problem.

---

### Post by rixtr66 on 2008-07-15
all better thank you!!
rick

---

