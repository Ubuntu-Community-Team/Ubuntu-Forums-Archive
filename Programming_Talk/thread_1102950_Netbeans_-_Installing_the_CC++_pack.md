---
title: "Netbeans - Installing the C/C++ pack"
date: 2009-03-22
forum: Programming Talk
---

### Post by JordyD on 2009-03-22
I decided to install Netbeans and give it a try. I installed it via the package manager, but it's not up-to-date, and I can't find the C/C++ pack in the repositories. I don't want to upgrade it, because I'm worried that that will confuse my package manager. So I have two questions:

1) Will upgrading it without using the package manager confuse the package manager when it tries to update it itself or when I try to uninstall it?

2) If I install the C/C++ pack, will that also confuse the package manager?

Thanks,
Jordy

---

### Post by crush304 on 2009-03-22
I've always just installed the latest version from netbeans.org, by default it installs in /usr/local/netbeans-... Then you can add plugins (c++ or other) through netbeans and they install in /home/your-user-name/.netbeans/...

this method should not have any effect on packages installed through the package manager

---

### Post by cl333r on 2009-03-22
I wanna second crush304, getting from the web is better (for me) also because NetBeans 6.5.1 is already out with latest fixes and enhancements. It has been changed to address the fixes from jdk 6 update 12 so in my case NetBeans running on top of jdk 6 update 12 seems snappier.

---

