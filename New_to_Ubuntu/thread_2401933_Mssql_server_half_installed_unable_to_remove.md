---
title: "Mssql server half installed unable to remove"
date: 2018-09-24
forum: New to Ubuntu
---

### Post by sobergem on 2018-09-24
sudo dpkg --force-remove-reinstreq --remove mssql-server

dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 206608 files and directories currently installed.)
Removing mssql-server (14.0.3037.1-2) ...
/var/lib/dpkg/info/mssql-server.postrm: 21: /var/lib/dpkg/info/mssql-server.postrm: systemctl: not found
dpkg: error processing package mssql-server (--remove):
 subprocess installed post-removal script returned error exit status 127
Processing triggers for libc-bin (2.19-0ubuntu6.14) ...
Errors were encountered while processing:
 mssql-server


unable to remove the above package

---

