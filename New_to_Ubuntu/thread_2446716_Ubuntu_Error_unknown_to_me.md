---
title: "Ubuntu Error unknown to me"
date: 2020-07-05
forum: New to Ubuntu
---

### Post by loybanks on 2020-07-05
Just recently installed Ubuntu inside my Windows 10 by using the WSL method using the Windows 10 cmd line box. After logging in I have received the following error message. I have no idea at this point in time what to do. So need some help here? Many thanks.    Loy Banks

loybanks@LBEnvy23:~$ sudo apt install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libc-bin (2.31-0ubuntu9) ...
Aborted (core dumped)
/sbin/ldconfig.real: Can't stat /usr/local/lib/x86_64-linux-gnu: No such file or directory
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib' given more than once
/usr/local/lib:
/lib/x86_64-linux-gnu:
Aborted (core dumped)
dpkg: error processing package libc-bin (--configure):
 installed libc-bin package post-installation script subprocess returned error exit status 134
Errors were encountered while processing:
 libc-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
loybanks@LBEnvy23:~$

---

### Post by TheFu on 2020-07-05
**sudo apt install** isn't a valid command. it needs 1 or more options, usually a list of packages to be installed.

i know nothing about WSL.  The sort of error shown implies that Linux isn't installed. Those locations are core to all Linux libraries.

May want to alter your sig. Politics aren't good in these forms.

---

### Post by ActionParsnip on 2020-07-06
You need to specify a package to install. Eg:
```

sudo apt install unp

```

As The Fu stated, your command is incomplete so will make errors. What are you actually trying to achieve? Are you wanting to run full system updates from the terminal?

---

