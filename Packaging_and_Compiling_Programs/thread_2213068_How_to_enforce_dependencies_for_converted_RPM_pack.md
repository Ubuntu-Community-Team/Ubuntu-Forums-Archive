---
title: "How to enforce dependencies for converted RPM packages"
date: 2014-03-24
forum: Packaging and Compiling Programs
---

### Post by William_LePera on 2014-03-24
Hi.  I am trying to determine how to enforce package dependencies in .rpm packages converted to .deb format with the alien tool.  I am using Ubuntu 12.04 and alien 8.86.

I have three packages I need to convert from .rpm to .deb.  I need to enable the following dependencies:
package_A has no dependencies
package_B is dependent on package_A *and* the xinetd package
package_C is dependent on package_B

One thing I found fairly quickly was the alien tool does not carry over any of the "Requires" entries from the .rpm's to the converted .deb packages.  I found that by using the -g flag, alien would create the necessary Debian packaging files and then stop.

So, the first command I ran was

```

alien -c package_A.rpm
```

This was successful.  Next, I ran

```

alien -c -g package_B.rpm
```

This was also successful.  The resulting debian/control file contained the following "Depends" line:

```

Depends: ${shlibs:Depends}
```

At this point, if I simply run "debian/rules binary" I can complete the packaging and get a functioning .deb file for package_B, but it doesn't look for any of my dependencies.  Next, I modified the control file to pick up the xinetd dependency:

```

Depends: ${shlibs:Depends}, xinetd
```

I successfully ran "debian/rules binary" to create a new package_B.deb which honors the xinetd dependency.  Finally, I added the dependency for package_A:

```

Depends: ${shlibs:Depends}, xinetd, package_A
```

Running "debian/rules binary" with this control file fails:

```

dpkg-gencontrol: warning: can't parse dependency package_A
dpkg-gencontrol: error: error occurred while parsing Depends field: , xinetd, package_A
dh-gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/package_B.substvars -Pdebian/package_B returned exit code 255
```

The file "debian/package_B.substvars" contains only one line:

```

misc:Depends=
```

I'm guessing the "xinetd" dependency worked because it referred to a native .deb package.  Is there a way to use the .deb packages converted from .rpm in the "Depends" control field?

---

### Post by tgalati4 on 2014-03-25
I think you need to go to the source files and repackage from scratch.  If these rpm's are binary blobs (proprietary code without source code) then you may be out of luck.  You can try to set up dummy debian packages to fake the dependencies, but you have already spent a lot of time on this.  How often would you need to update this system?  If *xinetd* is the only native dependency, then perhaps write a wrapper script for apt-get to check for those changes whenever an update is performed.  Not ideal, more of a hack, but easier than repackaging if you don't have the piece parts.

---

