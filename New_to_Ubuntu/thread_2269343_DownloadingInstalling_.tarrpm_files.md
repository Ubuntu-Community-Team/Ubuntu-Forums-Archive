---
title: "Downloading/Installing .tar/rpm files"
date: 2015-03-15
forum: New to Ubuntu
---

### Post by rob122 on 2015-03-15
Hi Folks, I'm a complete novice at this. I'm having no success in trying to install an application from

[https://aur.archlinux.org/packages/draftsight-legacy/](https://aur.archlinux.org/packages/draftsight-legacy/)

I've downloaded but not had much success in trying to extract the tarball and I see that an rpm file is mentioned
as source which leaves me confused as to what to do.

If anyone could give some step-by-step guidance it would be most appreciated.

---

### Post by buzzingrobot on 2015-03-15
Some basics:

1. Linux software is distributed in archives organized in a few standard ways.  There are a number of different formats for these achives, but they are all called, generically, *packages*. 

2.  Packages contain software files, other data, and scripts to ensure those software files are installed in the correct locations.

3. While package archives may be expanded, just like any other archive, that is not their intended use.

4. Linux distributions typically host software in packages on servers (repositories). Various tools, GUI and otherwise, are available to Linux users that access these repositories and allow software to be selected.  Once selected, a package will be downloaded and the software in it will be automatically installed by the *package manager* software used by the distribution.  If any other software is required by the package being installed, the package manager will locate, download and install those *dependencies* automatically.

5. The steps outlined above in #4 are mandatory for software installation.  Doing them manually, particularly identifying, locating, and correctly installing the correct dependencies (which can number in the dozens and up, and dependencies have their own dependencies, and so on) is an extremely tedious and error-prone process.  Package managers were developed years ago to deal with this problem.

6.  No single standardized package format or package manager is used throughout Linux. Ubuntu uses a package format called "deb" because those packages always have a ".deb" file extension.  Other distributions use ".rpm" files. Package managers that know about "deb" files do not know about "rpm" files.  That is, "deb" files can be installed using Ubuntu's package manager and "rpm" files cannot. And, vice versa on rpm distributions.

7. Arch is a distribution that distributes its packages in its own particular archive format that's different from both "deb" files and "rpm" files".  In addition, Arch packages contain source code, not compiled binary software. 

8.  *Your first resort for Ubuntu packages should be the Ubuntu repositories.*   Tens of thousands of packages are hosted there. The Software Center is provided as a store-like front end to the package manager and allows you to search, browse and install packages on those repositories.  Several other alternative front ends, of greater complexity and flexibility, are available in the Ubuntu repos.  "Synaptic" is popular.  The command-line tools -- apt-get, apt, etc. -- can also be use, of course.

9. *Avoid attempting to install software from tarballs and packages intended for "foreign" distributions. Avoid the Windows-like habit of installing software directly from an archive hosted on a vendor's or a developer's site.*  In the unlikely event that the attempt is successful, the package manager on your system will not know about this software. As a result, that software will not be automatically updated by the system updater; you will need to track the availability of updates and manually install them yourself. The "foreign" software may also create software incompatibilities, now or in the future.

---

### Post by arochester on 2015-03-15
There is a download for Ubuntu [http://www.3ds.com/products-services/draftsight-cad-software/free-download/](http://www.3ds.com/products-services/draftsight-cad-software/free-download/)

---

### Post by rob122 on 2015-03-15
Thanks for that.

I think that download from 3ds.com is a 64-bit version. I need the older 32-bit.

---

