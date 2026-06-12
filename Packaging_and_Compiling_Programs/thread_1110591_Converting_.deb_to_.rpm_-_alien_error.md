---
title: "Converting .deb to .rpm - alien error"
date: 2009-03-29
forum: Packaging and Compiling Programs
---

### Post by dodle on 2009-03-29
alien works fine if I download a .deb package and convert.  But when I try to convert a package that I've created, the build fails.  Here is the output of [COLOR="Red"]sudo alien -rck debreate_0.2-1beta_all.deb[/COLOR]:```
Package build failed. Here's the log of the command (cd debreate-0.2; rpmbuild -bb --target noarch debreate-0.2-2.spec):
error: line 1: Tag takes single token only: Buildroot: /home/user/Programming/Python/debreate versions/debreate-0.2
Building target platforms: noarch
Building for target noarch

```

Any ideas?  Here is my control file:```
Package: debreate
Version: 0.2-1beta
Section: Development
Priority: optional
Homepage: 
Architecture: all
Essential: no
Depends: python, python-wxgtk2.6 | python-wxgtk2.8, apt
Enhances: 
Pre-Depends: 
Recommends: 
Suggests: 
Installed-Size: 37.9
Maintainer:
Conflicts: 
Replaces: 
Provides: 
Description: Creates Debian Packages
 
 A tool to help make Debian packages
```

---

### Post by dodle on 2009-03-30
Fixed!  Apparently the problem was that I needed a period on the second line of the description in the control file:```
Package: debreate
Version: 0.2-1beta
Section: Development
Priority: optional
Homepage: 
Architecture: all
Essential: no
Depends: python, python-wxgtk2.6 | python-wxgtk2.8, apt
Enhances: 
Pre-Depends: 
Recommends: 
Suggests: 
Installed-Size: 37.9
Maintainer:
Conflicts: 
Replaces: 
Provides: 
Description: Creates Debian Packages
 .
 A tool to help make Debian packages
```

---

### Post by spatil on 2009-04-03
Hi i am not able to convert .deb to rpm by using following command

alien -r linux-image-2.6.20-17-generic_2.6.20-17.39_i386.deb

I am getting following error:-
Warning: Skipping conversion of scripts in package linux-image-2.6.20-17-generic: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log of the command (cd linux-image-2.6.20-17-generic-2.6.20; rpmbuild -bb --target i386 linux-image-2.6.20-17-generic-2.6.20-18.39.spec):
error: line 1: Tag takes single token only: Buildroot: /root/Desktop/Download/Images and src/linux-image-2.6.20-17-generic-2.6.20
Building target platforms: i386
Building for target i386

If i use following command
alien -r --scripts linux-image-2.6.20-17-generic_2.6.20-17.39_i386.deb

I am getting follwing eroor

Package build failed. Here's the log of the command (cd linux-image-2.6.20-17-generic-2.6.20; rpmbuild -bb --target i386 linux-image-2.6.20-17-generic-2.6.20-18.39.spec):
error: line 1: Tag takes single token only: Buildroot: /root/Desktop/Download/Images and src/linux-image-2.6.20-17-generic-2.6.20
Building target platforms: i386
Building for target i386


Please help me how can i convert it to rpm.

Thanks in advance....

---

### Post by dodle on 2009-04-03
I thought that I had this fixed, but apparently not.  Sometimes alien works for me, and sometimes I get the same exact error you describe.  I haven't been able to figure it out.

---

### Post by vnevoa on 2009-09-07
I had the error when the ".deb" package was sitting in a path with spaces and accentuated characters. After moving the deb to a shorter and simpler path, it worked just fine.

---

