---
title: "HOWTO: Obtain list of unsupported installed packages"
date: 2006-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2006-11-21
If you're maintaining Ubuntu systems for a production or other security-conscious, you'll probably want to know what packages are installed that a standard dist-upgrade won't cover security/support-wise. For example, packages from universe/multiverse, Backports, those not from repositories, checkinstalled/aliened packages, etc.

This is a simple Python script that lists the packages and version numbers of unsupported packages on your system. **You need grep-dctrl installed** to use this (which is ironically in universe)

```

#!/usr/bin/python
# apt-unsupported
# Prints out a list of ubuntu packages not officially supported
#
# Copyright (C) 2006 John Dong <jdong@ubuntu.com>
# 
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
#



import os
list1=set(os.popen('apt-cache dumpavail | grep-dctrl -nsPackage -FSection iverse/').readlines())
list2=set(os.popen('''dpkg --get-selections | awk '$2 == "install" { print $1 }' '''))
universe=list1.intersection(list2)
pkgs=universe.union(set(os.popen('''  dpkg -l | grep "~" | awk '{print $2}' ''').readlines()))
pkgs=list(pkgs)
pkgs.sort()

for i in pkgs:
    print "%-25s %s" % (i.strip(),os.popen('dpkg -s %s | sed -ne "s/Version: //p"' % i.strip()).read()),

```

Example Output:
```
jdong@server:/var/cache/torrentflux/jdong/Zod-binary-i386$ apt-unsupported adzapper                  20060115-1
apt-cacher                1.5.3~dapper1
arj                       3.10.22-2
bip                       0.5.0-1
clamav                    0.88.4-1ubuntu1~dapper1
clamav-base               0.88.4-1ubuntu1~dapper1
clamav-freshclam          0.88.4-1ubuntu1~dapper1
... Output Abbreviated ...

```

This is very handy, though far from perfect. Current glaring flaws:
  * Inaccurate backports checking: it just looks for a "~" in the version number, which most of the times means a backport.
  * Currently unable to identify packages installed from non-Ubuntu repositories, such as a 3rd party APT repository
  * Unable to identify packages that are locally installed (anyone know how to get Synaptic's Locally Installed/Obsolete output at the command line?)

If you have suggestions/improvements, please let me know!

---

### Post by ingo on 2006-11-22
this is a great idea! keep on developing, I'm right behind you :)

---

