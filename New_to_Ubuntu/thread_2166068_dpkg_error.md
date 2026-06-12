---
title: "dpkg error"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by umfunix on 2013-08-07
I don't know what happened when and where, but whatever apt-get command I issue, I get a dpkg error, similar like this one....

```
Unknown configuration key `foreign-architecture' found in your `dpkg'
configuration files.  This warning will become a hard error at a later
date, so please remove the offending configuration options and replace
them with `dpkg --add-architecture' invocations at the command line.


```

After a apt-get update I get this

```
Setting up obm-storage (2.1.10-0ubuntu2) ...
dbconfig-common: writing config to /etc/dbconfig-common/obm-storage.conf
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dpkg: error processing obm-storage (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of obm:
 obm depends on obm-storage (= 2.1.10-0ubuntu2); however:
  Package obm-storage is not configured yet.

dpkg: error processing obm (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 obm-storage
 obm
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Any help to fix this please!  Thanks

---

### Post by GwL3eNC on 2013-08-07
Hi,

whats in your /etc/dpkg/dpkg.cfg

On my system i found a string foreign-architecture in

/etc/dpkg/dpkg.cfg.d/multiarch.

I would try to do what the first text says. Or eventually a
sudo apt-get dist-upgrade may help.

---

### Post by umfunix on 2013-08-07
Hi, thanks for the help but I've tried that and then get the code I've posted above.  My /etc/dpkg/dpkg.cfg is empty.

---

### Post by GwL3eNC on 2013-08-07
Empty?

Thats mine:

# dpkg configuration file
#
# This file can contain default options for dpkg.  All command-line
# options are allowed.  Values can be specified by putting them after
# the option, separated by whitespace and/or an `=' sign.
#

# Do not enable debsig-verify by default; since the distribution is not using
# embedded signatures, debsig-verify would reject all packages.
no-debsig

# Log status changes and actions to a file.
log /var/log/dpkg.log

Have you seen my edit about the other file?

Ps: if in /var/lib/dpkg/info/ are scripts for 
obm, obm-storage

try renameing them. Think some new will be generated

---

