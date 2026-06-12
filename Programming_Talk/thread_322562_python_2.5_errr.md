---
title: "python 2.5 errr"
date: 2006-12-20
forum: Programming Talk
---

### Post by newsman on 2006-12-20
does anyone  have, had any problem with python 2.5

i tried reinstall python 2.5 because python gave me a lot of problems.....got error
 thus i tried from source i got error again


lreader.py ...
Compiling /usr/local/lib/python2.5/xmllib.py ...
Compiling /usr/local/lib/python2.5/xmlrpclib.py ...
Compiling /usr/local/lib/python2.5/zipfile.py ...
make: *** [libinstall] Error 1

---

### Post by newsman on 2006-12-20
Just went through apt-get remove and install again


the remove didn't go smoothly either:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
python-all python-dhm python2.5 idle-python2.5 python2.5-examples
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
idle-python2.5 python-all python-dhm python2.5 python2.5-examples
0 upgraded, 0 newly installed, 5 to remove and 22 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 16.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 182169 files and directories currently installed.)
Removing idle-python2.5 ...
Removing python-all ...
Removing python-dhm ...
Removing python2.5-examples ...
Removing python2.5 ...
Setting up python-constraint (0.3.0-5) ...
Compiling /usr/lib/python2.5/site-packages/logilab/constraint/propagation.py ...
File "/usr/lib/python2.5/site-packages/logilab/constraint/propagation.py", line 21
from __future__ import generators
SyntaxError: from __future__ imports must occur at the beginning of the file

pycentral: pycentral pkginstall: error byte-compiling files (Cool
pycentral pkginstall: error byte-compiling files (Cool
dpkg: error processing python-constraint (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
python-constraint
E: Sub-process /usr/bin/dpkg returned an error code (1)



The subsequent install via apt-get;

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
python-profiler
The following NEW packages will be installed:
python2.5
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
1 not fully installed or removed.
Need to get 0B/3241kB of archives.
After unpacking 12.0MB of additional disk space will be used.
Selecting previously deselected package python2.5.
(Reading database ... 180961 files and directories currently installed.)
Unpacking python2.5 (from .../python2.5_2.5-2ubuntu2_i386.deb) ...
Setting up python-constraint (0.3.0-5) ...
Compiling /usr/lib/python2.5/site-packages/logilab/constraint/propagation.py ...
File "/usr/lib/python2.5/site-packages/logilab/constraint/propagation.py", line 21
from __future__ import generators
SyntaxError: from __future__ imports must occur at the beginning of the file

pycentral: pycentral pkginstall: error byte-compiling files (Cool
pycentral pkginstall: error byte-compiling files (Cool
dpkg: error processing python-constraint (--configure):
subprocess post-installation script returned error exit status 1
Setting up python2.5 (2.5-2ubuntu2) ...

Errors were encountered while processing:
python-constraint
E: Sub-process /usr/bin/dpkg returned an error code (1)



This is the same error when doing a "reinstall" from synaptic package manager


Thus the attempt to compile from source


(I just went through that process again... same result)

---

