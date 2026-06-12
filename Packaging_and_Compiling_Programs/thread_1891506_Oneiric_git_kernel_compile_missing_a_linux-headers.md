---
title: "Oneiric git kernel compile missing a linux-headers package."
date: 2011-12-05
forum: Packaging and Compiling Programs
---

### Post by ptn107 on 2011-12-05
I compiled the latest Ubuntu 11.10 kernel from git (git://kernel.ubuntu.com/ubuntu/ubuntu-oneiric.git) using the following command:
> DEB_BUILD_OPTIONS=parallel=2 AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-debs

When the process is complete I have the following files:

linux-headers-3.0.0-14-generic_3.0.0-14.23_amd64.deb
linux-headers-3.0.0-14-server_3.0.0-14.23_amd64.deb
linux-headers-3.0.0-14-virtual_3.0.0-14.23_amd64.deb
linux-image-3.0.0-14-generic_3.0.0-14.23_amd64.deb
linux-image-3.0.0-14-server_3.0.0-14.23_amd64.deb
linux-image-3.0.0-14-virtual_3.0.0-14.23_amd64.deb
linux-image-extra-3.0.0-14-virtual_3.0.0-14.23_amd64.deb
linux-tools-3.0.0-14_3.0.0-14.23_amd64.deb

However I do not have a linux-headers-3.0.0-14_3.0.0-14.23_amd64.deb file which is required by the headers-$version-generic file.  How do I make one?

---

### Post by ptn107 on 2011-12-05
Fixed it by also doing:
```
DEB_BUILD_OPTIONS=parallel=2 AUTOBUILD=1 NOEXTRAS=1 skipabi=true fakeroot debian/rules binary-indep
```

---

