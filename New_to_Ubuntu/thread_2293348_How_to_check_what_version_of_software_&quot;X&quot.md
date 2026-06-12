---
title: "How to check what version of software &quot;X&quot; is available on next Ubuntu release?"
date: 2015-09-04
forum: New to Ubuntu
---

### Post by 9dor on 2015-09-04
Hi,

I would like to know:
How do I check what version of software named "X" is available on next Ubuntu release?

In my case, X="wallch".

You see, I have the following problem that I reported on wallch's launchpad:
[https://bugs.launchpad.net/wallpaper-changer/+bug/1492179](https://bugs.launchpad.net/wallpaper-changer/+bug/1492179)

So I was told to completely un-install "wallch" (which was installed via Ubuntu Software Center), becuase its version was pretty much old.

That is why I want to check whether the next Ubuntu release has the recent "wallch" version, which is "4.187-0~213~ubuntu14.04.1" (or newer).
In Ubuntu Software Center, the available wallch version is "wallch 4.0-0ubuntu4".

Thank you! :D

---

### Post by howefield on 2015-09-04
Even Wily (the current development version) has Package: wallch (4.0-0ubuntu4) [universe]

---

### Post by 9dor on 2015-09-04
> **howefield said:**
> Even Wily (the current development version) has Package: wallch (4.0-0ubuntu4) [universe]

Thanks!

_I have 2 questions:_
[LIST=1]
[*]How did you check that?
[*]How do I ask Ubuntu developers team to include the recent version of "wallch"?
Should exist a place where people ask the developers for stuff?
[/LIST]

---

### Post by howefield on 2015-09-04
> **9dor said:**
> How did you check that?

I am running the development version but you can also check out packages.ubuntu.com

> How do I ask Ubuntu developers team to include the recent version of "wallch"?

There is a developers mailing list, the package maintainers is listed on the .deb package as Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

You could also hunt out a ppa with the latest version although this would be a third party package, for example [https://launchpad.net/~wallch/+archive/ubuntu/wallch-4.0](https://launchpad.net/~wallch/+archive/ubuntu/wallch-4.0) looks like it contains the version you are after. There may be others. By giving you this link, it is not an endorsement, only one that I found by searching.

---

### Post by 9dor on 2015-09-04
> **howefield said:**
> I am running the development version but you can also check out packages.ubuntu.com



There is a developers mailing list, the package maintainers is listed on the .deb package as Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

You could also hunt out a ppa with the latest version although this would be a third party package, for example [https://launchpad.net/~wallch/+archive/ubuntu/wallch-4.0](https://launchpad.net/~wallch/+archive/ubuntu/wallch-4.0) looks like it contains the version you are after. There may be others. By giving you this link, it is not an endorsement, only one that I found by searching.

I'd rather install directly from the official PPAs.

So I'll send an email to "ubuntu-devel-discuss@lists.ubuntu.com", asking them to include the recent "wallch" version.

Thanks for your help!

---

### Post by howefield on 2015-09-04
> **9dor said:**
> I'd rather install directly from the official PPAs.

+1 Good luck.

---

### Post by Geoffrey_Arndt on 2015-09-04
OR, you can always install it from the source code . . . just get the required dev support package (it's something like "build-essential or build-essentials".   Then read the install instructions at the source web site (launchpad, git, or the developers own sites).

---

