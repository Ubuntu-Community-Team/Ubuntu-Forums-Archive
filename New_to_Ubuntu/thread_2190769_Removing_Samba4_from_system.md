---
title: "Removing Samba4 from system"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by pacian on 2013-11-29
While trying to install another package (synaptic) I received the following messages below...

Running 13.10 Ubuntu..
I am trying to 

1. remove samba and its dependencies
2. install synaptic ...

it is clear to me that SAMBA 4 did not properly install and I WANT to remove all of it from my system..
thank you.


Error message found below
_________________________________________________________________________________________________
Setting up samba4 (4.0.3+dfsg1-0.1ubuntu1) ...
ERROR(ldb): uncaught exception - operations error at ../source4/dsdb/samdb/ldb_modules/rootdse.c:501
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/dbcheck.py", line 108, in run
    fix=fix, yes=yes, quiet=quiet, in_transaction=started_transaction)
  File "/usr/lib/python2.7/dist-packages/samba/dbchecker.py", line 62, in __init__
    self.ntds_dsa = samdb.get_dsServiceName()
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 856, in get_dsServiceName
    res = self.search(base="", scope=ldb.SCOPE_BASE, attrs=["dsServiceName"])
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
pacian@pacian-linux:~$ sudo apt-get remove --purge getdeb-repository
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getdeb-repository
pacian@pacian-linux:~$ sudo apt-get remove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba4 (4.0.3+dfsg1-0.1ubuntu1) ...
ERROR(ldb): uncaught exception - operations error at ../source4/dsdb/samdb/ldb_modules/rootdse.c:501
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/dbcheck.py", line 108, in run
    fix=fix, yes=yes, quiet=quiet, in_transaction=started_transaction)
  File "/usr/lib/python2.7/dist-packages/samba/dbchecker.py", line 62, in __init__
    self.ntds_dsa = samdb.get_dsServiceName()
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 856, in get_dsServiceName
    res = self.search(base="", scope=ldb.SCOPE_BASE, attrs=["dsServiceName"])
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mikewhatever on 2013-11-29
How did you install samba 4?

---

### Post by pacian on 2013-12-01
resolved thanks

---

### Post by mörgæs on 2013-12-01
Please post the solution and mark the thread 'solved'.

---

### Post by rossocomeillambrusco on 2014-01-02
Post please, I have the same issue

---

### Post by sampayu on 2014-05-18
I suggest you install Synaptic:

**```
sudo apt-get install synaptic
```**
...then run Synaptic and mark (select) the **samba** DEB package for removal. Also select all the other packages of the _same version_ of the **samba** package (see their versions on the "Installed version" column). You'll most probably end up having to remove these packages along with the **samba** one:

samba-common

samba-common-bin

samba-libs

samba-doc

system-config-samba

smbclient

libsmbclient

python-samba

cifs-utils

Click "Apply" and Synaptic will remove your packages. If it removes extra packages that you didn't want removed (like k3b, software-center and/or vlc), just mark these packages again and reinstall them. In Synaptics you can go to File => History and see which packages were uninstalled, then all you have to do is to recover what you want back.;)

---

