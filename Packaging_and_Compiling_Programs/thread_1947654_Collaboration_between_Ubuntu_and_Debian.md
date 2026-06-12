---
title: "Collaboration between Ubuntu and Debian"
date: 2012-03-27
forum: Packaging and Compiling Programs
---

### Post by zradu on 2012-03-27
I make same patches (in my branch) for one application in Ubuntu that have been merged, now I want to submitt this patches back to Debian (this is fair). How to make this, is there any tutorial for this job?

Thanks and regards.

---

### Post by MadCow108 on 2012-03-27
the tool "submittodebian" from ubuntu-dev-tools is useful for forwarding changes to debian, the manpage describes the process which you can also do manually
to report a bug in debian use reportbug -B debian

make sure the patch also applies to the debian package.

---

### Post by zradu on 2012-03-27
OK,
Thanks for clarification.

---

