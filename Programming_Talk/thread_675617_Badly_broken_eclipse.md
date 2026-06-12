---
title: "Badly broken eclipse"
date: 2008-01-22
forum: Programming Talk
---

### Post by meridian100 on 2008-01-22
Hi,
I somehow broke my eclipse sometime in the past while, and tonight while attempting to fix it I may have broken it worse. 

I get an error whenever I try to start it, and I've attached the error log.

Any help or advice you could give me would be amazing as I'm a tad green at linux and am at a loss.

Thank you very much

---

### Post by naugiedoggie on 2008-01-23
> **meridian100 said:**
> Hi,
I somehow broke my eclipse sometime in the past while, and tonight while attempting to fix it I may have broken it worse. 

I get an error whenever I try to start it, and I've attached the error log.

Any help or advice you could give me would be amazing as I'm a tad green at linux and am at a loss.

Thank you very much

Hello,

Well, there is always the uninstall/reinstall route.  Eclipse should not be storing any mission-critical data in the install directories, unless you specified your workbench location there (unlikely).  The uninstaller will not remove your .eclipse or workbench directories (but you can rename them for safety).  After a reinstall, all your config and source files should be right where you left them, and should impact the new installation.

Judging by the number of problems that people have with eclipse, it is not the most stable IDE for those just starting out.  You might want to look at [NetBeans]("http://www.netbeans.org") for an alternative.  In my experience, you just install it and it works.  The interface is much more intuitive than Eclipse, and you don't need a uni course to figure out how to code in it.  (But, I've been using it for years, so undoubtedly I'm prejudiced.)

Thanks.

mp

---

### Post by jeremytaylor on 2008-01-24
You could try starting it with the -clean flag

i.e. eclipse -clean

Jeremy

---

