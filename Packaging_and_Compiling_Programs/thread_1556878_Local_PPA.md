---
title: "Local PPA"
date: 2010-08-20
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-08-20
Dear all,

I created a local PPA with mini-dinstall, using the configuration files ~/.dput.cf and ~/.mini-dinstall.conf from here: [https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository) except for the fact that I use as archive: /var/cache/archive

Everything seems to work fine:
```

dput -U local ../robot3d-data_0.1-0ubuntu2_source.changes 

Package includes an .orig.tar.gz file although the debian revision suggests that it might not be required. Multiple uploads of the .orig.tar.gz may be rejected by the upload queue management software.
Uploading to local (via local to localhost):
Successfully uploaded packages.
/usr/lib/pymodules/python2.6/minidinstall/misc.py:21: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  import os, errno, time, string, re, popen2
mini-dinstall [140473481565968] ERROR: Failed to verify signature on "/var/cache/archive/mini-dinstall/incoming/robot3d-data_0.1-0ubuntu2_source.changes": 'gpgv exited with error code 2'
gpgv: keyblock resource `/usr/share/keyrings/debian-keyring.pgp': file open error
gpgv: Signature made Fri 20 Aug 2010 12:40:54 AM EDT using RSA key ID 66666666
gpgv: Good signature from "Anne van Rossum (Roboticist) <some@email.com>"

  robot3d-data has no source override entry
  robot3d-data has no binary override entry either

```

It indeed shows up in /var/cache/archive/lucid: the tarball, the description file (dsc), source.changes and the diff.gz. Also, I added a symlink to from /var/cache/archive to /var/www/archive and added [http://localhost/archive](http://localhost/archive) lucid/ to /etc/apt/sources.list. The repository seems to be found.

**Problem**
My problem is that the Packages file in /var/cache/archive/lucid seems to be **empty**! The Sources file in contrary contains information:
> 
Package: robot3d-data
Binary: robot3d-data
Version: 0.1-0ubuntu2
Maintainer: Anne van Rossum <some@email.com>
Build-Depends: debhelper (>= 7)
Architecture: any
Standards-Version: 3.8.4
Format: 1.0
Directory: lucid


In debian/control I have both a Source: robot3d-data as well as a Package: robot3d-data paragraph.

I used "bzr builddeb -S" to build it.

When I upload to the PPA on Launchpad everything works fine: [http://ppa.launchpad.net/robot3d-team/ppa-robot3d/ubuntu/dists/lucid/main/binary-amd64/Packages](http://ppa.launchpad.net/robot3d-team/ppa-robot3d/ubuntu/dists/lucid/main/binary-amd64/Packages)

Is this a bug in mini-dinstall? Or are the configuration files I use from [https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository) outdated?

Thanks in advance!

Anne

---

