---
title: "Items cannot be installed or removed"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by fergyan on 2013-05-13
sorry if my english is bad :) i am new here. sorry if i am wrong :(
i just want to know what happen to my distros.

i open terminal and type sudo apt-get install -f
```

fergyan@Fergyan:~$ sudo apt-get install -f
[sudo] password for fergyan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libxmmsclient6 libid3tag0 libimlib2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  visualboyadvance
The following NEW packages will be installed:
  visualboyadvance
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/297 kB of archives.
After this operation, 1,364 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 307600 files and directories currently installed.)
Unpacking visualboyadvance (from .../visualboyadvance_1.8.0.dfsg-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/visualboyadvance_1.8.0.dfsg-0.1_i386.deb (--unpack):
 trying to overwrite '/etc/VisualBoyAdvance.cfg', which is also in package vbam 0.svn451-1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/visualboyadvance_1.8.0.dfsg-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Whats wrong ? :( anyone want to help me ? because i am new on ubuntu :(
thank you.

---

### Post by sandyd on 2013-05-13
**moved to ABT**

---

### Post by Frogs Hair on 2013-05-13
The program visualboyadvance has not been updated since 2009, so it would have run in 9.10. I think that may be the problem.  [http://vba.ngemu.com/](http://vba.ngemu.com/)

---

### Post by fergyan on 2013-05-13
> **Frogs Hair said:**
> The program visualboyadvance has not been updated since 2009, so it would have run in 9.10. I think that may be the problem.  [http://vba.ngemu.com/](http://vba.ngemu.com/)


i just want to remove it but ubuntu software center keeps show items cannot be installed or removed until package catalog is repaired. i'll try to repair it but it crash "package operation failed"

---

### Post by ibjsb4 on 2013-05-13
This may work

In terminal (one line at a time):

```
sudo dpkg -r visualboyadvance
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
```

---

