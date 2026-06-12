---
title: "DEB Control file - architecture all for 32 + 64 bit"
date: 2011-02-23
forum: Packaging and Compiling Programs
---

### Post by Jacks0n on 2011-02-23
Hi there

I'm in the process of packaging an application for Ubuntu. It's compiled as 32 bit (Qt app) and I won't be shipping a 64 bit version (the app isn't CPU intensive, there's no real benefit).

With Windows and Mac I can ship one installer and it'll run on 32 bit and 64 bit machines even though the binary's 32 bit. With Ubuntu I noticed I must make two DEB packages, one for 32 bit and one for 64 bit. When I build the deb, if I set in the control file the architecture to "all", will this let 32 bit and 64 bit users run the 32 bit file? I realize people with other architectures won't be able to, but none of my users will have anything but x86. Also do 64 bit users need ia32 libs? Or is that only for some other 32 bit apps on 63 bit platforms? Thanks!

---

### Post by MadCow108 on 2011-02-23
first of all, why not ship a 64 bit version?
If the program does not work, fix it.
I find it very annoying when a library pulls in the gigantic security risk which is ia32libs ...

to build a 32 bit package for 64 bit systems you need to specify the architecture, set up the build system to always compile 32 bit versions and get all the dependencies right e.g.:
```

Source: ...
Build-Depends: debhelper (>= 4), libpng12-dev | libpng-dev, xlibmesa-gl-dev, libao-dev, ia32-libs [amd64], lib32z1-dev [amd64], lib32stdc++6 [amd64], gcc-multilib [amd64], g++-multilib [amd64]

Package: ...
Architecture: i386 amd64
Depends: ${shlibs:Depends}

```

---

### Post by Jacks0n on 2011-02-23
It has a self-update mechanism built into it, it'd add more complexity to it when it's just not necessary. The program isn't CPU intensive, so there's no benefit of having a 64 bit version.

So is ia32libs essential to run a 32 bit binary on a 64 bit machine in Ubuntu? I'd like to make a package that's compatible for both CPU types. I don't know what ia32libs is for, I'm guessing it links the libraries? What if I ship a version with 32 bit libraries in the same directory?

---

### Post by MadCow108 on 2011-02-23
64 bit has not much to do with performance, it is more about supporting the most used platform today, and that is 64 bit. You almost do not get any 32 bit desktop pcs anymore.

ia32libs is a gigantic package containing many 32 bit versions of libraries for 64 bit systems (copied from i386 builds).
These are required to run 32 bit programs which cannot use the system 64 bit libraries.
These 32bit libraries are updated far less frequently, especially security updates are often delayed considerably.

not all libraries are included in that package, if the ones you need are not included you either need to ask the maintainers to add it (which they will only do if its really important) or ship it with your package.
both is strongly discouraged. Better fix your software to work with 64bit.

One option concerning the autoupdate would be to disable it and update it over the package manager (e.g. via a ppa, or an own external repo via /etc/apt/sources.list.d/ (see opera))

---

### Post by Jacks0n on 2011-02-23
Hm okay, interesting.. Thanks for your comments. We're just a startup, so I can't justify making a PPA/repo yet. I'll avoid the use of ia32libs though!

---

