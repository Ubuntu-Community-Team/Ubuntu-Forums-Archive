---
title: "dpkg vs rpm for previously installed packages"
date: 2014-05-22
forum: Packaging and Compiling Programs
---

### Post by William_LePera on 2014-05-22
I am converting some RPM packages to .deb format using alien.  While testing, I am seeing some differences in behavior between dpkg and rpm when a package is installed over itself.  For example, if I were to do "rpm -i foo_a-1.0.0.rpm" on a machine where foo_A-1.0.0 was already installed, rpm would write a message about the pre-existing package and quit.  With dpkg, when I do "dpkg -i foo_A-1.0.0.deb" on a machine where foo_A-1.0.0 is already installed, the behavior is different.  It looks like:

1) package prerm and postrm scripts are loaded.  prerm is executed
2) package is unpacked, overwriting all files (including the pre and post install
   and uninstall scripts)
3) previously loaded postrm is executed.  This causes some vital files to be removed.
4)The newly unpacked postinst script is run.  This script tries to perform operations on
   some of the files that were remoed in step 3 above.  This causes the install to fail
   and leaves the .deb package in a broken state.

I get the same result if I use "gdebi" instead of "dpkg -i". 

Is this normal dpkg behavior?  I don't know if there was something in the conversion from rpm that may have caused this.  Is there a way to mimic the rpm behavior so that the package simply doesn't install?  Or must we re-write our pre-and post install/remove scripts (which were written based on how RPM worked) to be more "Debian-friendly"?

---

### Post by tgalati4 on 2014-05-22
Unfortunately, that may be the case.  Pre and post installation scripts allow a lot of flexibility for installing all kinds of packages, but that makes migrating packages from one framework to another difficult.  One can weigh the agony units of packaging software from scratch into Debian (if all the source is available).  If the software has binary blobs (compiled for Red Hat exclusively), then the conversion may not work at all.

As a learning experience, take one of the rpm packages that is giving you problems (the smallest package that you can find), look for all the source code for that package then try your hand at creating a clean, from scratch Debian package.  It's time consuming but not that difficult.  The most difficult part is getting a consistent build environment for your endpoint.  Trying to compile code that works in a 2.6.XX kernel may be difficult to get to work in a 3.5.XX or 3.11.XX environment.

Burrow as deeply as you care to go:  [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

As for your immediate problem:  dpkg has a -G switch which is supposed to prevent installing an older version of a package if a newer version is already installed.  I don't know how it behaves if the same version of the package exists.  My guess is that it will overwrite and try to reinstall the same version of the package.  In that case, pre and post installation scripts could trip up the process if key files are deleted that are needed for configuration.  Using *dpkg purge packagename* should remove all configuration files to give a clean start, but then again pre and post install files could leave some crumbs.

---

### Post by William_LePera on 2014-05-22
Thank you for your response.  We will evaluate generating native Debian packages.  Using alien was appealing because it looked like it would allow us to avoid maintenance of two packaging formats.

Also, the dpkg option to mimic the RPM behavior I was looking for is -E:

```
# dpkg -iE foo_A-1.0.0.deb
dpkg: version 1.0.0 of foo_A already installed, skipping
# 
```

---

### Post by tgalati4 on 2014-05-22
I was not aware of the -E option.  Alien is a neat solution for small or simple packages.  If it works, great.  If not, then you have some work to do.

If you are a software provider (and it sounds like you are) then yes, that is the cost of supporting different distributions.  If you look around at popular packages, some are packaged for Ubuntu, some for Ubuntu, Debian, Red Hat.  Others are just source and you can build them yourself--the most simplistic distribution model.  

If you need help packaging software for Ubuntu or Debian, then just ask, there are lots of folks with packaging experience.  I would not rely on *alien* for creating packages for wide distribution.  It's strictly a roll-your-own tool for getting something from a Red Hat distro to work in a Debian distro without too much pain.  If it doesn't work out-of-the-box, then pain is in your future.  No way around that.

There are a lot of tools available in the Debian packaging universe, but not many to go from Red Hat to Debian because of the way libraries are bundled.

For instance if a Red Hat package has only one dependency (say libraryABC) then the Debian version may have 3 dependencies (LibraryA, LibraryB, and LibraryC).  The reason for splitting them out is so that development can happen faster on individual libraries and the frameworks that are built using these libraries is always changing.  For Red Hat (because of its corporate heritage), the development happens on a corporate time scale, so the packaging reflects that.  

I had a Dell PowerEdge 1750 server that I installed Ubuntu on.  There are a lot of neat Red Hat utilities that work on that server, but they were not packaged for Ubuntu.  I used *alien* to convert a few of them and they worked.  For the ones that didn't work, I searched the web and found custom-compiled Debian packages that installed just fine.  So I saved myself some agony units.  

If you are supporting two different Linux distributions (Debian-based and Red Hat-based), then there is really no way around learning the packaging methods of both distributions.  That pain is measured in Agony Units.  When AU exceed your tolerance, you find something else to do.

---

