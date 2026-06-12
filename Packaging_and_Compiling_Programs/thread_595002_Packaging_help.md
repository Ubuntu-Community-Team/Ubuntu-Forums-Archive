---
title: "Packaging help"
date: 2007-10-28
forum: Packaging and Compiling Programs
---

### Post by davidsiegel on 2007-10-28
I'm working on an application right now, and it's available as a tarball download from my website. I'd like to make a package available for Ubuntu. Is there anywhere I can find a mentor for this, or is there a place where I can find someone who will package it for me?

---

### Post by mlind on 2007-10-28
> **davidsiegel said:**
> I'm working on an application right now, and it's available as a tarball download from my website. I'd like to make a package available for Ubuntu. Is there anywhere I can find a mentor for this, or is there a place where I can find someone who will package it for me?

Ubuntu wiki contains very good resources if you're starting from scratch and there's also ongoing mentoring program for new packagers.

[https://help.ubuntu.com/ubuntu/packagingguide/C/](https://help.ubuntu.com/ubuntu/packagingguide/C/)
[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
[https://wiki.ubuntu.com/MOTU/Documentation](https://wiki.ubuntu.com/MOTU/Documentation)
[https://wiki.ubuntu.com/MOTU/Mentoring/Reception](https://wiki.ubuntu.com/MOTU/Mentoring/Reception)

What type of program (language) you're packaging?

---

### Post by davidsiegel on 2007-10-28
[http://launchpad.net/gc](http://launchpad.net/gc)

It's mono/C#. I'm going to try to befriend someone who is familiar with this process. Hey, nice bean count... haha

---

### Post by mlind on 2007-10-29
> **davidsiegel said:**
> [http://launchpad.net/gc](http://launchpad.net/gc)

It's mono/C#. I'm going to try to befriend someone who is familiar with this process. Hey, nice bean count... haha

If you cannot find a mentor, I can also help you out. By looking how some mono apps like banshee or f-spot are packaged, you can get a feeling how to begin.

---

### Post by mlind on 2007-10-29
I took a test how this package would turn out and and I'm attaching the resulting source package, including a binary for Gutsy.

The package builds okay on Gutsy on Feisty and installs in Gutsy. I didn't actually try to run the binary though. I tested only the tarball from your site, dunno if this works with the code in bzr.


Some notes I made during the process
> 
[LIST]
[*] src/Do.UI/MainMenu.cs contains version string '0.1', so package is versioned after that.
[*] 'debianized' tarball must have version number in top level directory.
[*] Packaging is based a bit on banshee and f-spot. You should also check Debian CLI Policy draft ([http://pkg-mono.alioth.debian.org/cli-policy/](http://pkg-mono.alioth.debian.org/cli-policy/))


[*] debian/copyright: you should probably review the information here and fix anything that's not okay.
[*] debian/control: binary package description should be written to be more useful
[*] debian/watch: not actually working, but left in as an example
[/LIST]


About certain Build-Depends in debian/control
[LIST]
[*] cli-common-dev (>= 0.4.4)
  - required to provide dh_clifixperms and dh_clideps used in debian/rules
  - dh_clideps will automatically generate required mono dependencies (replacing ${cli:Depends})

[*] libgnome-vfs2.0-cil | gnome-sharp
  - allows package to build in feisty too. feisty's gnome-sharp2 is not splitted and there's no libgnome-vfs2.0-cil

[*] libgnome-desktop-dev
  - for .desktop integration I guess ? This drags along quite many other dependencies, so drop if not needed.
  - in build time there's a warning aboout libgnome-desktop-2.so.2 if package is not installed. 
[/LIST]

gnome-do binary now Recommends tomboy, should this be Depends ? (is tomboy required for gnome-do to work properly?)


See also:
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
[https://perso.duckcorp.org/duck/cdbs-doc/cdbs-doc.xhtml](https://perso.duckcorp.org/duck/cdbs-doc/cdbs-doc.xhtml)
[http://www.ambienteto.arti.beniculturali.it/cgi-bin/man2html?debhelper+1](http://www.ambienteto.arti.beniculturali.it/cgi-bin/man2html?debhelper+1)
[http://pkg-mono.alioth.debian.org/cli-policy/](http://pkg-mono.alioth.debian.org/cli-policy/)
[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)



I hope this helps.

---

### Post by davidsiegel on 2007-10-29
You're amazing. I can't wait to test these out and let you know the results.

Yes, for now Tomboy is a dependency because I use libtomboy. I will try learn what the other things you mentioned mean and whether or not they should be included. Every package you named is something we use, so it all sounds right.

Thanks again. I'll let you know later today about my results.

---

### Post by mlind on 2007-10-29
> **davidsiegel said:**
> You're amazing. I can't wait to test these out and let you know the results.

Yes, for now Tomboy is a dependency because I use libtomboy. I will try learn what the other things you mentioned mean and whether or not they should be included. Every package you named is something we use, so it all sounds right.

Thanks again. I'll let you know later today about my results.

okay, then you need to change tomboy from Recommends to Depends in debian/control.

Here's a very quick howto for compiling the binaries:
[LIST]
[*]download the attached archive and extract it, say in **/tmp/test.** You can remove the binary (gnome-do_0.1-0ubuntu1_i386.deb) as you will compile your own.

[*]install **dpkg-dev** (to get *dpkg-source*) and then extract the source package:
```

sudo aptitude install dpkg-dev
dpkg-source -x gnome-do_0.1-0ubuntu1.dsc

```

[*]review files in the gnome-do-0.1/**debian**/ directory. Everything else is (and should remain) untouched. Change **tomboy** from Recommends to **Depends** in **debian/control** for gnome-do binary.
Recommends will probably be empty then, so you can remove the whole line.


[*]install **devscripts** package to get useful tools package management tools, like **dch**. Then use dch to create new changelog entry. You need to be in the folder which has the debian directory when executing dch. Bump the version to 0ubuntu**2** and document your changes (like "debian/control: Depends instead of Recommends tomboy"):
```

sudo aptitude install devscripts
dch -i

```

[*]To build the package you can use e.g **dpkg-buildpackage -us -uc**, but using autobuilder like [**pbuilder**]("https://wiki.ubuntu.com/PbuilderHowto") or sbuild is probably more convenient as those resolve build dependencies automatically.
[/LIST]

If you have any questions just ask.

---

### Post by davidsiegel on 2007-10-29
Thank you for your excellent example and instructions, however it's all still magic to me.

```
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5) cdbs autotools-dev cli-common-dev (>= 0.4.4) libgnome-desktop-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

```

I will try pbuilder when I have a more reliable connection, but why are these dependencies if I don't have them, yet I can build the project?

---

### Post by mlind on 2007-10-29
> **davidsiegel said:**
> Thank you for your excellent example and instructions, however it's all still magic to me.

```
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5) cdbs autotools-dev cli-common-dev (>= 0.4.4) libgnome-desktop-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

```

I will try pbuilder when I have a more reliable connection, but why are these dependencies if I don't have them, yet I can build the project?

debhelper and cdbs contain helper scripts for the packaging process. I guess most (if not all) packages in Ubuntu and Debian build-depend on debhelper. Answer to the question why to use debhelper and cdbs should be explained in the links I posted earlier.

autotools-dev provides up-to-date config.guess and config.sub for automake and libtool (cdbs automatically symlinks these files to correct place during build).

cli-common-dev contains additional debhelper scripts for mono packages.

libgnome-desktop-dev is only required to provide /usr/lib/libgnome-desktop-2.so.2. I guess you could replace it by libgnome-desktop-2 if you need only this library.
Dependency could be removed completely if it's not needed during build, but there was some sort of warning without it.

---

### Post by bapoumba on 2007-10-31
Moved to the "Packaging" sub-forum.

---

### Post by g2g591 on 2007-11-01
pbuilder is the only accepted form of packages unfortunatly (it has clean envrionment that only installs explictly stated packages in the build-deps and you can have pbuilders for releases like hardy which hasn't even come out yet

---

