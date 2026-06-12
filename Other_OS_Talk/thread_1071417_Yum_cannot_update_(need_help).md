---
title: "Yum cannot update (need help)"
date: 2009-02-16
forum: Other OS Talk
---

### Post by crazysexycool on 2009-02-16
I get the following error when i try to update typing in yum update i am using centos 5.2 in a VM on IBM thinkpad T61P 

I can use the internet and i am behind a proxy hope somone can help here is my CentOS-Base file.

[root@jf3252485-2066 yum.repos.d]# ls
CentOS-Base.repo  CentOS-Base.repo.save  CentOS-Media.repo
[root@jf3252485-2066 yum.repos.d]# cat CentOS-Base.repo
# CentOS-Base.repo
#
# This file uses a new mirrorlist system developed by Lance Davis 
for CentOS.
# The mirror system uses the connecting IP address of the client and 
the
# update status of each mirror to pick mirrors that are updated to 
and
# geographically close to the client.  You should use this for 
CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can 
try the 
# remarked out baseurl= line instead.
#
#



[base]
name=CentOS-$releasever - Base
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os
baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/
gpgcheck=1
gpgkey=http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-5
priority=1
protect=1
enabled=1

#released updates 
[update]
name=CentOS-$releasever - Updates
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates
baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/
gpgcheck=1
gpgkey=http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-5
priority=1
protect=1

#packages used/produced in the build but not released
[addons]
name=CentOS-$releasever - Addons
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=addons
baseurl=http://mirror.centos.org/centos/$releasever/addons/$basearch/
gpgcheck=1
gpgkey=http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-5
priority=1
protect=1

#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras
baseurl=http://mirror.centos.org/centos/$releasever/extras/$basearch/
gpgcheck=1
gpgkey=http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-5
priority=1
protect=1

#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus
baseurl=http://mirror.centos.org/centos/$releasever/centosplus/$basearch/
gpgcheck=1
enabled=0
gpgkey=http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-5
priority=2
protect=1

#contrib - packages by Centos Users
[contrib]
name=CentOS-$releasever - Contrib
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib
baseurl=http://mirror.centos.org/centos/$releasever/contrib/$basearch/
gpgcheck=1
enabled=0
gpgkey=http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-5
priority=2
protect=1


[root@jf3252485-2066 yum.repos.d]#

---

### Post by crazysexycool on 2009-02-16
Please can someone help me with this.

---

