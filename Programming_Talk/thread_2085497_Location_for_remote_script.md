---
title: "Location for remote script"
date: 2012-11-18
forum: Programming Talk
---

### Post by 233x on 2012-11-18
Hello,
I want to install a script on one host in a LAN. This script shall be accessible to multiple remote client users who execute this script via rsh/ssh. Where should this script be located? Thanks in advance.

---

### Post by MG&amp;TL on 2012-11-18
Anyway you like on the server, if I understand you correctly. Although convention is for one of the locations in the $PATH environment variable.

---

### Post by 233x on 2012-11-20
To be more precise: I would like to know if this script shall be located in /bin, usr/bin or some other directory.

---

### Post by Lars Noodén on 2012-11-20
They usually go in /usr/local/bin.  If they are for system administration, they go in /usr/local/sbin.  The details of what goes where is covered in [hier(7)](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html)

---

