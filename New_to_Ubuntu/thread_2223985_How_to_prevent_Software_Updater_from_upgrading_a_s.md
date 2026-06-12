---
title: "How to prevent Software Updater from upgrading a single software install"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by greatkingrat2 on 2014-05-13
I installed a package from the software developers where there's also a Debian package in the standard repositories for the same software.  Every time software updater runs it tells me I should upgrade that software.  In this case, I prefer the upstream version.

Is there any way I can tell the update mechanism to ignore that package in the repositories?

---

### Post by deadflowr on 2014-05-13
Perhaps the easiest way is through synaptic package manager.

Install synaptic, open > go to the section "origin" > then local (as the package should be a locally install package).
Find the package, highlight it, and in the menu click on "Package", go to lock version.
Now it should be set.

---

### Post by greatkingrat2 on 2014-05-14
Thank you! I knew that had to exist somewhere, but I could not find the proper set of search terms to find it.

---

### Post by deadflowr on 2014-05-14
Having thought a little more about this, a package installed through a third party deb, shouldn't be getting updates from the Ubuntu repos. Reason being that the Ubuntu repos look for/use very specific names of packages.

Something to look for is the possibility that the installed package added a ppa to the system, which would be how the package would otherwise be getting updates.
In the application "Software and Updates, look at the section for other software.
See if there are any entries there that might be connected to the installed package.
If so, then simply uncheck it, which will stop the package from getting updates.

---

### Post by HiImTye on 2014-05-14
that's not necessarily true, apt compares the version numbers and if they're greater it will upgrade them. the only exception is when the version strings are so different that it can't make heads or tails of it (I can't remember off the top of my head, but one piece of software has a version string that is impossible to create with checkinstall)

generally, though, Ubuntu doesn't bump software up to the next major version unless there's a serious flaw in the previous one

---

