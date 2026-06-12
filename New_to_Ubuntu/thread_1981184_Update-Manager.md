---
title: "Update-Manager"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by devrat43 on 2012-05-16
This is the message I get whenever I open **Update-Manager**.(Ubuntu Software Center doesn't open either).

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

**'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'**

---

### Post by cortman on 2012-05-16
> **devrat43 said:**
> This is the message I get whenever I open **Update-Manager**.(Ubuntu Software Center doesn't open either).

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

**'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'**

Quick easy fix- in a terminal-

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

This just replaces the package list files.

---

### Post by devrat43 on 2012-05-16
Thank you.

---

### Post by cortman on 2012-05-16
> **devrat43 said:**
> Thank you.

You're welcome- mark as [SOLVED] using the thread tools in the upper right. Thanks, and good luck!

---

### Post by Njorl on 2012-09-24
Very happy to have found this helpful thread, as I encountered this problem today.

Perhaps an apt-get command for deleting the lists would facilitate us non-experts in clearing the problem quickly and safely.  (I'd tried "clean" and "purge" before turning to the Internet.)

Sudo recursive remove isn't something we (non-experts) should, ordinarily, feel happy to enter.  However, the specific command line, provided by cortman, looked correct, in the context of the problem, and worked for me - with no adverse effects noticed, so far.

Grateful thanks.

---

### Post by nopedx on 2012-09-28
That's why I love Ubuntu - had same problem, this "fixed" it.
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update

thanks cortman i.e. = This just replaces the package list files.

---

### Post by nopedx on 2012-09-28
> **cortman said:**
> Quick easy fix- in a terminal-

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

This just replaces the package list files.
cortman thanks!

---

