---
title: "Standalone Ubuntu source code access"
date: 2010-01-03
forum: Packaging and Compiling Programs
---

### Post by reanimator on 2010-01-03
Hi,

Sorry for silly question. But I can't figure out how to get the access to the latest source code of Ubuntu. I would like to check some patches applied by Ubuntu community, but can't find them.

Do I really need to use .deb packages to get the sources or there are some CGit or ViewCVS like interfaces?

Thanks!

---

### Post by adelphos on 2010-01-03
Do you mean the Ubuntu-modifed Linux kernel? This might be helpful:

[https://help.ubuntu.com/community/Kernel/Compile#Get%20the%20kernel%20source](https://help.ubuntu.com/community/Kernel/Compile#Get%20the%20kernel%20source)

Beyond that, you can get the source for individual packages by using " apt-get source <packagename>"

---

### Post by reanimator on 2010-01-05
Thanks for reply.

This almost what I looking for. In fact I would like to check the XFCE related patches.

Do you have a idea where to search?

---

### Post by adelphos on 2010-01-05
[http://packages.ubuntu.com/karmic/xfce4](http://packages.ubuntu.com/karmic/xfce4)

Under "Related Packages" there, they list a lot of the XFCE packages. You could use "apt-get source" for the ones you want to look at, I think.

---

### Post by reanimator on 2010-01-05
[SOLVED]

Thanks a lot!

I have also found the patches itself here:
[http://archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-sensors-plugin/](http://archive.ubuntu.com/ubuntu/pool/universe/x/xfce4-sensors-plugin/)

---

### Post by andrewsomething on 2010-01-05
There are a number of options, but if you still would like one that is CGit or ViewCVS like, Ubuntu packages are also found in Bazaar branches. You can look at them in Loggerhead via Launcpad. For instance, you seem to be interested in xfce4-sensors-plugin, so look here:

[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/lucid/xfce4-sensors-plugin/lucid/files](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/lucid/xfce4-sensors-plugin/lucid/files)

You generally browse to there from:

[https://code.launchpad.net/ubuntu/+source/xfce4-sensors-plugin](https://code.launchpad.net/ubuntu/+source/xfce4-sensors-plugin)

---

