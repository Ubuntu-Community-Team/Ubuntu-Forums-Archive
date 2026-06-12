---
title: "trouble installing spam assassin"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by furoido on 2008-05-15
Can anyone resolve this please?


andrew@andrew-desktop:~$ sudo apt-get install spamassassin
[sudo] password for andrew:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
spamassassin: Depends: libdigest-sha1-perl but it is not installable
Depends: libarchive-tar-perl (>= 1.23) but it is not installable
Depends: libnet-dns-perl (>= 0.58) but it is not going to be installed
Depends: libio-zlib-perl (>= 1.04) but it is not installable
Depends: libmail-spf-perl but it is not going to be installed
E: Broken packages

---

### Post by Vadi on 2008-05-19
Go to System - Administration - Software Sources, and enable (main), (universe), (restricted), and (multiverse). Does the installation work after?

---

