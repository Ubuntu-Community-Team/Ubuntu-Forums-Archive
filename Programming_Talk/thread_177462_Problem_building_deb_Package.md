---
title: "Problem building deb Package"
date: 2006-05-16
forum: Programming Talk
---

### Post by Eremit on 2006-05-16
When building a deb package with dpkg-buildpackage the package is installed temporary under /home/blabla/packagename-1.0/debian/packagename/.....
Then dpkg-buildpackage uses this subfolder structure to create the deb package.

My problem is that the absolute folders get stored for later use in some files of the program. So after installing the .deb package all files are in the right place but the programm assumes wrong folders.

example:
/usr/share/pixmaps/packagename/test.xpm

but the program thinks the file is located at:
/home/blabla/packagname-1.0/debian/packagename/usr/share/pixmaps/packagename/test.xpm

example:
/usr/share/pixmaps/packagename/test.xpm

but the program thinks the file is located at:
/home/blabla/packagname-1.0/debian/packagename/usr/share/pixmaps/packagename/test.xpm

What's the correct solution for this problem?

*edit* 
Just saw there's an extra subforum - sorry
maybe someone could move it there thanks

---

