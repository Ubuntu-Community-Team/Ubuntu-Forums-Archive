---
title: "Padre Installation problem"
date: 2011-06-05
forum: Programming Talk
---

### Post by sudoalb on 2011-06-05
I installed Padre (Perl Editor) but I am unable to open it.

I installed it using the info at [this]("http://padre.perlide.org/download.html") page.

The error I get is:

> Can't load '/usr/lib/perl5/auto/Wx/Wx.so' for module Wx: /usr/lib/perl5/auto/Wx/Wx.so: symbol wxDefaultVideoMode, version WXU_2.8 not defined in file libwx_gtk2u_core-2.8.so.0 with link time reference at /usr/lib/perl/5.10/DynaLoader.pm line 192.
 at /usr/share/perl5/Padre/TaskThread.pm line 23
Compilation failed in require at /usr/share/perl5/Padre/TaskThread.pm line 23.
BEGIN failed--compilation aborted at /usr/share/perl5/Padre/TaskThread.pm line 23.
Compilation failed in require at /usr/share/perl5/Padre/Startup.pm line 113.

Any help? 

thx

---

### Post by cgroza on 2011-06-05
I have this problem too. No one seems to address this problem seriously.

---

### Post by sudoalb on 2011-06-05
> **cgroza said:**
> I have this problem too. No one seems to address this problem seriously.

Have you contacted the developers?

---

### Post by cgroza on 2011-06-05
> **sudoalb said:**
> Have you contacted the developers?
I do not have the required information to do that.

---

### Post by SevenMachines on 2011-06-05
Should be fixed soon
[https://bugs.launchpad.net/ubuntu/+source/libwx-perl/+bug/754513](https://bugs.launchpad.net/ubuntu/+source/libwx-perl/+bug/754513)

---

### Post by sudoalb on 2011-06-06
> **SevenMachines said:**
> Should be fixed soon
[https://bugs.launchpad.net/ubuntu/+source/libwx-perl/+bug/754513](https://bugs.launchpad.net/ubuntu/+source/libwx-perl/+bug/754513)

Thx for the link. I tried some of the instructions given there but impossible. 
Anyway, hope it will be ok soon.

---

### Post by SevenMachines on 2011-06-07
its entered natty-proposed if you want to test the fix
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

---

