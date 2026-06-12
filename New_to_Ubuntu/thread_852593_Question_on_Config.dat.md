---
title: "Question on Config.dat"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by bcschmerker on 2008-07-07
During package installs and/or updates on my Everex gPC, Synaptic Package Manager and Package Upgrader both call XDebConfigurator during the post-download package installation.  A common error is returned:
> /var/cache/debconf/config.dat is locked by another process - Resource temporarily unavailable
What processes require /var/cache/debconf/config.dat; and can the SPM runtime script be amended to defeat XDebConfigurator without injuring some other portion of the install process?  A location for the SPM script would be helpful, provided the XDebConfigurator defeat can be done safely.

---

### Post by ZabiGG on 2008-07-09
Hi. This appears to be related to an old bug. Did you google your error message?

Z.

---

### Post by bcschmerker on 2008-07-10
I found the page on LinuxForums.org about the error in question:
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
During the SPM Apply Changes script, frontend locks the file to do its job, thus the denial of resource to /usr/sbin/debconf.  A whole bunch of SBins may reference Config.dat, so I should've expected this issue, given my experience with occasional Process conflicts in MS-Windows (viz., multiple .EXE and/or .DLL binaries attempting to access the same data simultaneously).

What Debian packages are relevant to the requisite bug fix; and how should I proceed with post-install Configuration?

---

