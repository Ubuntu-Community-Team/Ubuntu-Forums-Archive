---
title: "samba upgrade issue"
date: 2006-07-16
forum: Repositories &amp; Backports
---

### Post by DJ-Power on 2006-07-16
Hi I am having a problem with my system now where it tells me that I have broken packages and so I cant install any updates.
The terminal gives this on running sudo apt-get install -f

Preconfiguring packages ...
(Reading database ... 110218 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am at a loss what to do. If I run package manager in synaptic and choose the option to fix the broken package when I try to install at the end I egt the same result.

Regards

---

### Post by David Oxland on 2006-07-25
-

---

### Post by David Oxland on 2006-07-25
Same problem for me

---

