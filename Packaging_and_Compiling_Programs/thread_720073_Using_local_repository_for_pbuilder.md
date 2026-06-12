---
title: "Using local repository for pbuilder"
date: 2008-03-09
forum: Packaging and Compiling Programs
---

### Post by farruinn on 2008-03-09
I've followed the PbuilderHowto and the PackagingGuide/Complete wiki pages, but when I attempt to update my pbuilder to use a local repository it ignores the local repo and so I can't build some packages that depend on packages not in ubuntu or debian.

```

$ sudo pbuilder update \
--bindmounts /var/cache/archive/ \
--override-config --othermirror "deb file:///var/cache/archive/ gutsy/"

[sudo] password for nathan:
Upgrading for distribution gutsy
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /var/cache/archive
 -> policy-rc.d already exists
Refreshing the base.tgz 
 -> upgrading packages
Ign file: gutsy/ Release.gpg
Ign file: gutsy/ Release
Ign file: gutsy/ Packages 

```

However when I login to the pbuilder chroot the files are there:
```
root@ubuntu:/# ls /var/cache/archive/gutsy/
Packages                              libmxp1_0.2.2-0ubuntu1_amd64.deb
Packages.gz                           libmxp_0.2.2-0ubuntu1.diff.gz
Sources                               libmxp_0.2.2-0ubuntu1.dsc
Sources.gz                            libmxp_0.2.2-0ubuntu1_amd64.changes
libmxp1-dev_0.2.2-0ubuntu1_amd64.deb
```

---

### Post by pablaasmo on 2008-05-05
Hi,
I have the same problem as this.
Was there any soulution to this?

Regards
Per A.

---

### Post by loeppel on 2008-06-24
Same Problem here.
This is the reason why backporting php5.2 to dapper fails!
See [thread]("http://ubuntuforums.org/showthread.php?t=574406").

Any solution to this?

greets,
loeppel

---

