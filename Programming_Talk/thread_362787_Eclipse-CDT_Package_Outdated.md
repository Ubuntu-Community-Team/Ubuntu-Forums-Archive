---
title: "Eclipse-CDT Package Outdated?"
date: 2007-02-16
forum: Programming Talk
---

### Post by stromb on 2007-02-16
Hi all,

I'm no programmer, but wanted to start self-educating myself on C using Eclipse and the CDT plugin. However, when I installed the eclipse and eclipse-cdt (ver. 3.0.1-3) packages via synaptic, I keep getting "Error notifying a preference change listener" errors when opening Eclipse. I have read multiple threads elsewhere showing this to be an incompatibility between the CDT plugin version I have and the current Eclipse version (ver. 3.2.1). I have also confirmed this by removing the CDT plugin and finding that all works fine without it.

I see the latest CDT version is now 3.1.1 according to the Eclipse website (since Sept.), so my questions are: is there some place I can obtain a newer .deb package for CDT (as I havn't been able to locate any) and why has Ubuntu not updated this package in their main repositor[y,ies]? I would think this would be a fairly popular package and find it odd to not have been updated to a newer package that has been out since September.

Thanks in advance!

---

### Post by stromb on 2007-02-16
Okay, I found an updated package here:

[http://us.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse-cdt/](http://us.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse-cdt/)

---

### Post by locutus42 on 2007-03-07
> **stromb said:**
> Okay, I found an updated package here:

[http://us.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse-cdt/](http://us.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse-cdt/)

this worked, thanks. FYI, I used the builtin Eclipse update function to update Eclipse to version 3.2.2 and hoped it would also allow for updating of CDT but it didn't and left CDT at v3.0.?. Downloading the latest CDT from your US archive link and installing it with:

sudo dpkg -i ./eclipse-cdt_3.1.1-0ubuntu2_i386.deb

worked like a charm.

Tested main.cpp( helloworld ) compiling and debugging and it all worked.
Thanks again for mentioning the link.

---

