---
title: "snort-mysql installation error"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by scribbles on 2008-11-23
After running ```
sudo apt-get install snort-mysql
```
I get this: ```
Setting up snort-mysql (2.7.0-19ubuntu1) ...
 * Stopping Network Intrusion Detection System  snort * No running snort instance found
 * Starting Network Intrusion Detection System  snort * /etc/snort/db-pending-config file found
 * Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort-mysql (--configure):
 subprocess post-installation script returned error exit status 6
Setting up oinkmaster (2.0-2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 snort-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)
:~#
```

What would cause this? :confused:

---

### Post by spiderbatdad on 2008-11-23
[http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10)

---

### Post by m42h31 on 2009-07-22
i found same problem,  the problem come from your old snort-mysql configuration.but i found solution for it.
please edit this file /etc/default/snort
find ALLOW_UNAVAILABLE="no" 
than edit "no" with "yes" 
ALLOW_UNAVAILABLE="yes"
than run : dpkg --configure --pending
and than: dpkg-reconfigure snort-mysql

after finish with new configuration, try to start the snort daemon
service snort start

* Starting Network Intrusion Detection System snort                                               [ OK ]

---

