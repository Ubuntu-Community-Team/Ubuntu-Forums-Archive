---
title: "Could not initialize the package information"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by lynyl on 2012-08-07
I found this error message when opening the computer. At first I couldn't access the internet, but now I can.

**[SIZE="2"][B]Could not initialize the package information**[/SIZE][/B]

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header,    E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

This usually means that your installed packages have unmet dependencies.

**So, after reading this, I ran apt-get check:**

lyn@lynslinux:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

[B]Questions:[B] 1. What do I do to correct this problem?
                 2. Do I have to create a root account and sign 
                    in as root?
I am a Linux beginner, so spell out all the steps!  Thanks!

---

### Post by Kalanac on 2012-08-07
do

```
sudo apt-get update
```

type in your usual password.

That should fix it.  It was just the repos being unable to update because of the lack of internet connection.  The apt-get check failed because you didn't use sudo and therefore didn't have root privelage.

---

### Post by lynyl on 2012-08-07
Thanks - that did it!!

---

