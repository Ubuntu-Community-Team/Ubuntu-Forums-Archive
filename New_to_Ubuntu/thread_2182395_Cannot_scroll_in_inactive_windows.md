---
title: "Cannot scroll in inactive windows"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Anshul_Joshi on 2013-10-21
[B]hi. 
i've recently installed ubuntu 13.10 and im unable to scroll in any inactive windows

how can i enable this funtion , it worked just fine in ubuntu 13.04
Please help[/B]

---

### Post by againsttcpa84 on 2013-10-24
Hi,
this bug is known in [launchpad]("https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1240957"). There is not much you can do, exept wait until the fix comes with some updates. But I think it might take a while... :|
A developer offers a PPA with a fix to test it, but I do not recommend this to anyone who is not an expert!

Btw, only GTK windows are affected, LibreOffice, Firefox, etc. work as expected.

---

### Post by Anshul_Joshi on 2013-10-24
Thanks for replying 
i thought there won't be any reply to this thread 

im a beginner in ubuntu so i cannot try what you have suggested 
and i haven't tested it on firefox or libreoffice yet , i only wanted to use it in document viewer to scroll pdfs

---

### Post by mc4man on 2013-10-24
This can be fixed (i believe) by reverting or subverting a gtk commit
Both Chris & I have ppa's that do so, it's related to these 2 bug reports
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1184159](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1184159)
[https://bugs.launchpad.net/compiz/+bug/1200829](https://bugs.launchpad.net/compiz/+bug/1200829)

My ppa reverts the commit & will continue to do so until this is fixed on all accounts, both in 13.10 & 14.04 if need be
[https://launchpad.net/~mc3man/+archive/test-scroll](https://launchpad.net/~mc3man/+archive/test-scroll)

---

