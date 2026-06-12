---
title: "Need a package that contains full featured libGLw.so"
date: 2007-02-28
forum: Programming Talk
---

### Post by mdc5712 on 2007-02-28
I have an programming framework from a vendor that requires a full featured libGLw.so. Specifically, it needs to include GLwCreateM2DrawingArea. Normally, this framework is used on Fedora Core, but I would like to use it on Ubuntu. I have tried the the *mesa* packages but they don't provide this routine. Anyone have any ideas?

---

### Post by hod139 on 2007-03-01
> **mdc5712 said:**
> I have an programming framework from a vendor that requires a full featured libGLw.so. Specifically, it needs to include GLwCreateM2DrawingArea. Normally, this framework is used on Fedora Core, but I would like to use it on Ubuntu. I have tried the the *mesa* packages but they don't provide this routine. Anyone have any ideas?
Looks like you might have found a [bug]("https://launchpad.net/ubuntu/+source/xfree86/+bug/38624").

---

### Post by kingcarl on 2008-05-27
1) Try downloading the libGLw.tar.gz from the miscellaneous category under the Mesa3D site on SourceForge:
[http://sourceforge.net/project/showfiles.php?group_id=3&package_id=27802](http://sourceforge.net/project/showfiles.php?group_id=3&package_id=27802)

2) Unpack the library and symbolic links and move them into /usr/lib/  or /usr/local/lib/  or whatever (make sure the ownership and permissions are set properly).


This worked for me with Ubuntu 8.04 Hardy Heron on x86-32 (2.6.24-16-generic #1 SMP Kernel) so I could run the AFNI neuro-imaging software from here: [http://afni.nimh.nih.gov/afni/](http://afni.nimh.nih.gov/afni/)

Cheers,
Carl

---

