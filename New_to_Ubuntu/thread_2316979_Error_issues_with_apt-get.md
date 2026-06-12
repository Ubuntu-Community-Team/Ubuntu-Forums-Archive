---
title: "Error issues with apt-get"
date: 2016-03-12
forum: New to Ubuntu
---

### Post by korn16ftl3 on 2016-03-12
so im trying to start a server up i chose Ubuntu 14.0.4.4 LTS as my operating system. after installation I immediately installed KDE as a GUI mostly so i can use things like web browsers and things of that nature to look up set-up guides and things of that nature.
At this point im trying to make my second HDD with all my media network accessible so i begin following the guide located here: [http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/) 

I get all the way to the point where it requests me to input the following: ```
[COLOR=#333333][FONT=Monaco]sudo apt-get install libnss-winbind winbind[/FONT][/COLOR]
``` at this pont the readout of the command prompt is as follows:

```
korn16ftl3@WORKGROUP:~$ sudo apt-get install libnss-winbind winbindReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  attr libhdb9-heimdal libkdc2-heimdal libpam-winbind python-dnspython
  python-ntdb python-samba python-tdb samba samba-common-bin
  samba-dsdb-modules samba-vfs-modules tdb-tools
Suggested packages:
  bind9 bind9utils ldb-tools ntp smbldap-tools heimdal-clients
The following NEW packages will be installed:
  attr libhdb9-heimdal libkdc2-heimdal libnss-winbind libpam-winbind
  python-dnspython python-ntdb python-samba python-tdb samba samba-common-bin
  samba-dsdb-modules samba-vfs-modules tdb-tools winbind
0 upgraded, 15 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,951 kB/3,334 kB of archives.
After this operation, 25.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libhdb9-heimdal python-samba samba-common-bin samba-dsdb-modules
  libkdc2-heimdal samba winbind libnss-winbind libpam-winbind
  samba-vfs-modules
Install these packages without verification? [y/N] y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libhdb9-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main python-dnspython all 1.11.1-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main samba-dsdb-modules amd64 2:4.1.6+dfsg-1ubuntu2.14.04.13
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main tdb-tools amd64 1.2.12-1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libkdc2-heimdal amd64 1.6~git20131207+dfsg-1ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main attr amd64 1:2.4.47-1ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main samba-dsdb-modules amd64 2:4.1.6+dfsg-1ubuntu2.14.04.13
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main samba amd64 2:4.1.6+dfsg-1ubuntu2.14.04.13
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main winbind amd64 2:4.1.6+dfsg-1ubuntu2.14.04.13
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe libnss-winbind amd64 2:4.1.6+dfsg-1ubuntu2.14.04.13
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe libpam-winbind amd64 2:4.1.6+dfsg-1ubuntu2.14.04.13
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main samba-vfs-modules amd64 2:4.1.6+dfsg-1ubuntu2.14.04.13
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libhdb9-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libhdb9-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'


E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dnspython/python-dnspython_1.11.1-1build1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dnspython/python-dnspython_1.11.1-1build1_all.deb)  Could not resolve 'us.archive.ubuntu.com'


E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-dsdb-modules_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-dsdb-modules_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb)  Could not resolve 'security.ubuntu.com'


E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tdb/tdb-tools_1.2.12-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tdb/tdb-tools_1.2.12-1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'


E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libkdc2-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/heimdal/libkdc2-heimdal_1.6~git20131207+dfsg-1ubuntu1.1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'


E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb)  Could not resolve 'security.ubuntu.com'


E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb)  Could not resolve 'security.ubuntu.com'


E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/s/samba/libnss-winbind_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/samba/libnss-winbind_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb)  Could not resolve 'security.ubuntu.com'


E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/s/samba/libpam-winbind_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/samba/libpam-winbind_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb)  Could not resolve 'security.ubuntu.com'


E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/attr/attr_2.4.47-1ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/attr/attr_2.4.47-1ubuntu1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'


E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-vfs-modules_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-vfs-modules_4.1.6+dfsg-1ubuntu2.14.04.13_amd64.deb)  Could not resolve 'security.ubuntu.com'


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

how do i resolve this problem or at least get to the bottom of what is going on here?

---

### Post by pauljw on 2016-03-12
Did you try running 'sudo apt-get update' ?  This should be done prior to attempting to install any software to insure the latest repos are being used.

---

