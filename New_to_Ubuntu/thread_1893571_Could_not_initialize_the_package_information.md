---
title: "Could not initialize the package information"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by Deepak H R on 2011-12-10
Hi

 I installed Ubuntu 11.04 today and as I tried to update my system by Update Manager it showed following error.

-----------------------------------------------------------------------------------------------------------------------
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

-----------------------------------------------------------------------------------------------------------------------

I'm new to this OS. Please suggest.
Thanks in advance

---

### Post by yeats on 2011-12-10
This thread may help:

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by Rubi1200 on 2011-12-11
See post # 4 in the thread yeats linked to for the solution.

The first command removes corrupted package lists, the second one refreshes them.

Let us know if this helps.

---

