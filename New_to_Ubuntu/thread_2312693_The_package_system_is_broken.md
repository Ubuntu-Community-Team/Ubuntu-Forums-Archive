---
title: "The package system is broken"
date: 2016-02-06
forum: New to Ubuntu
---

### Post by bekirs on 2016-02-06
Hi,

When I try to install new updates, I receive the following message:

***********************************
The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The following packages have unmet dependencies:


libnl-genl-3-200: Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
libnl-route-3-200: Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
***********************************

I typed **apt-get install -f**. The output is:
```

:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Do you know how to solve this issue?

---

### Post by pauljw on 2016-02-06
try "sudo apt-get install -f"  without the quotes of course.

---

### Post by bekirs on 2016-02-06
```

:~$ sudo apt-get install -f


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libmpdec2 libupstart1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnl-3-200
The following packages will be upgraded:
  libnl-3-200
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 0 B/45.8 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1183040 files and directories currently installed.)
Preparing to unpack .../libnl-3-200_3.2.21-1ubuntu1_amd64.deb ...
Unpacking libnl-3-200:amd64 (3.2.21-1ubuntu1) over (3.2.21-1) ...
Setting up libnl-3-200:amd64 (3.2.21-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...



```

---

### Post by bekirs on 2016-02-06
The issue is solved after following pauljw's solution.

Thanks

---

