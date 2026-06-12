---
title: "gimp upgrade"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Rbchound on 2008-09-20
Ubuntu Hardy 64bit

I have gimp 2.4.5

I want to upgrade to gimp_2.4.7-1~getdeb1_amd64.deb

How to install to include all dependencies required?

---

### Post by jcwmoore on 2008-09-20
download the file and double click it.  I believe the package manager will then try to install the dependencies (from the repositories)  you should not have any issues unless that version of gimp is dependent on something not in the repositories, like a new version of something not in the hardy repositories.  if it does not install dependencies, the gdeb installer can show you all the depended packages, you can install them through symantic

EDIT: the gimp from getdeb is dependent on the other .deb's you see on the getdeb.net page, download and install them before you actually install the you listed above

---

### Post by Rbchound on 2008-09-20
Thanks JCWMoore,

I did as you suggested.  I downloaded all packages and then installed one at a time. Worked great.

---

