---
title: "SAMBA not working and Nautilus does'nt shows the network Ubuntu 17.04"
date: 2017-05-01
forum: New to Ubuntu
---

### Post by migueltadeo01 on 2017-05-01
Audacious, economic :lolflag:.

I've started this week in the Ubuntu World and is fascinating.
 
Installed Ubuntu 17.04 but SAMBA didn't work and Nautilus was not able to see the network.

After two days of googling solved with this simple command lines

```


sudo apt-get remove samba samba-common system-config-samba python-minimal python python-glade2 python-dnspython python-samba gksu winbind smbclient samba-testsuite samba-vfs-modules registry-tools samba-testsuite registry-tools smbclient samba-common-bin libsmbclient libpam-winbind samba-common-bin libsmbclient libpam-winbind samba-libs tdb-tools python samba-libs samba-dsdb-modules tdb-tools logrotate samba-dsdb-modules

sudo apt-get install samba samba-common system-config-samba python-minimal python python-glade2 python-dnspython python-samba gksu winbind smbclient samba-testsuite samba-vfs-modules registry-tools samba-testsuite registry-tools smbclient samba-common-bin libsmbclient libpam-winbind samba-common-bin libsmbclient libpam-winbind samba-libs tdb-tools python samba-libs samba-dsdb-modules tdb-tools logrotate samba-dsdb-modules

sudo smbpasswd -L -a USER
PASSWORD
sudo smbpasswd -L -e USER


```

---

