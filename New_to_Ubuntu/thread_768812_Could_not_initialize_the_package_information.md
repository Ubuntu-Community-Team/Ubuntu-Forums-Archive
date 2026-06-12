---
title: "Could not initialize the package information"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by bobafifi on 2008-04-26
I just installed 8.04 but am getting this alert when I try to use Update Manager (see below).  Anybody know what I need to do to fix this?  Many thanks in advance. -Bob

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by hermes0710 on 2008-04-26
> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_bina ry-i386_Packages

There is a space between bina ry. Don't know where is this line though... Did you manually added repository?

---

### Post by bobafifi on 2008-04-26
I just copied and pasted the alert -- the dash (-) got removed somehow.  Here it is again:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing libqdbm3++c2 (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by jboy012000 on 2008-04-26
im not sure what the problem could be, i would just report the bug and keep looking through the forums, someone will know.

good luck.

---

### Post by hermes0710 on 2008-04-26
Post the output of:

```
sudo cat /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages 
```

---

