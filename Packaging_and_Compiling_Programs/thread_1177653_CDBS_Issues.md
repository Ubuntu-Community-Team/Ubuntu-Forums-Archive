---
title: "CDBS Issues"
date: 2009-06-03
forum: Packaging and Compiling Programs
---

### Post by flyguy97 on 2009-06-03
All,

I have a small, mostly Python, program which I uses a simple makefile to compile. I want to switch over to CDBS for creating debs to make maintenance easier but I don't think my makefile is setup to take advantage of CDBS. I can get the program to create a deb file but when I try to install the package the only files that are present are the ones generated when I run dh_make, all my application files are absent. the only messages that pop-up during dpkg-buildpackage is a bunch of warnings like the following:

```
dpkg-source: warning: ignoring deletion of directory locale
```

That seems to explained by the fact that my makefile creates these files/directories during make. I am including a zip of everything I have up to this point. Any help with this would be greatly appreciated.

Cheers,
Jason

---

