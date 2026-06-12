---
title: "how does the firefox in ubuntu compiled"
date: 2007-05-12
forum: Programming Talk
---

### Post by yinglcs2 on 2007-05-12
Hi,

Can you please tell me how does firefox in ubuntu compiled? 
I mean where can I find the .mozconfig file for mozconfig for the firefox in ubuntu?

I find that the firefox in ubuntu is faster than the firefox I run with Fedora 5.  I am running the same machine but with 2 different Linux OS.

Thank you.

---

### Post by seamless on 2007-05-13
You can download all the source for any Ubuntu package from [http://packages.ubuntu.com]("http://packages.ubuntu.com"). For Firefox speciffically, [http://packages.ubuntu.com/feisty/web/firefox]("http://packages.ubuntu.com/feisty/web/firefox"). However this likely not an issue with how Firefox was compiled but because you are using two different OS's. Fedora has a number of changes SELinux running for instance which can create a noticeable performance difference. You would probably be better off asking in a Fedora specific forum about turning Fedora to make it a bit faster. SELinux even in permissive mode will still slow down the system.

---

