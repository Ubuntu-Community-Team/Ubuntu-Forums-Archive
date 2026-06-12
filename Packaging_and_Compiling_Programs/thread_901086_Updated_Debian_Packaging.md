---
title: "Updated Debian Packaging"
date: 2008-08-26
forum: Packaging and Compiling Programs
---

### Post by Kruti Shah on 2008-08-26
Hi!!
Tamirs explanation in [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003) regarding creating a debian packaging has been really helpful.It will be great if someone can explain updating the debian package stepwise the  same way or can  suggest me with some good links which will help me out to know how to update a debian package and also how to make sure that through apt-get the updated package only will be installed..

Thanks for the help..

---

### Post by Kruti Shah on 2008-08-26
I got the answer:
You have to follow the following steps
1)cp -r debian/ to unpacked source
2)dch -i
3)dpkg-buildpackage -rfakeroot

---

