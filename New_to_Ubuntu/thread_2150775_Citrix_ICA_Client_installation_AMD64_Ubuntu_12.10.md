---
title: "Citrix ICA Client installation AMD64 Ubuntu 12.10"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by ravimn on 2013-06-02
Have anybody tried successfully installing Citrix ICA Client on Ubuntu 12.10 running on AMD64.  I am stuck at the step where I am trying to install nspluginwrapper which in turn needs nspluginviewer.  I am able to find installation for nspluginviewer only for x86 architecture.

---

### Post by handheld-penguin on 2013-06-07
Install from the deb and its all done for you. There are problems with icaclient on x86_64 : [http://ubuntuforums.org/showthread.php?t=2033947](http://ubuntuforums.org/showthread.php?t=2033947) . You have to modify the postinst file. Pretty straightforward actually. The plugin for firefox is installed automatically.

---

