---
title: "Permission denied while building package"
date: 2013-09-05
forum: Packaging and Compiling Programs
---

### Post by devongarber1 on 2013-09-05
This might be a dumb question but, I am trying to build a version of kubuntu-settings that I modified so that I can put it on a customized live cd, and every time I run dpkg-buildpackage on it, I just get this: ```
[COLOR=#000000]plymouth/kubuntu-logo/: Permission denied[/COLOR] 
dh_install: problem reading debian/plymouth-theme-kubuntu-logo.install
[COLOR=#000000]make: *** [binary] Error 126
[/COLOR][COLOR=#000000]dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2[/COLOR]
```
I've already checked the permissions and they look fine. I've only built four packages successfully so I'm new to this.

---

