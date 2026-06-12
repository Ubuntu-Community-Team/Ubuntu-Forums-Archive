---
title: "VirtualBox"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by levchv on 2011-09-21
Hi.
I can't install VirtualBox:

The following packages have unmet dependencies:

virtualbox-ose-qt: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
                   Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is to be installed
                   Depends: libqt4-opengl (>= 4:4.7.0~rc1) but 4:4.7.2-0ubuntu6 is to be installed
                   Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libstdc++6 (>= 4.5) but 4.5.2-8ubuntu4 is to be installed
                   Depends: virtualbox-ose (= 4.0.4-dfsg-1ubuntu4.1) but 4.0.4-dfsg-1ubuntu4.1 is to be installed

I can't also install any qt package.
I have Ubuntu 11.04 and use gnome.

---

### Post by haqking on 2011-09-21
> **levchv said:**
> Hi.
I can't install VirtualBox:

The following packages have unmet dependencies:

virtualbox-ose-qt: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
                   Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is to be installed
                   Depends: libqt4-opengl (>= 4:4.7.0~rc1) but 4:4.7.2-0ubuntu6 is to be installed
                   Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libstdc++6 (>= 4.5) but 4.5.2-8ubuntu4 is to be installed
                   Depends: virtualbox-ose (= 4.0.4-dfsg-1ubuntu4.1) but 4.0.4-dfsg-1ubuntu4.1 is to be installed

I can't also install any qt package.
I have Ubuntu 11.04 and use gnome.

Thats the old version in the repos, go to [www.virtualbox.org](www.virtualbox.org) and download the .deb for your system.  Also grab the extension pack also.  Or grab the ppa to update for latest version

---

### Post by levchv on 2011-09-22
Thanks. But I decided remove that packages and virtual box was abled to install.

---

### Post by haqking on 2011-09-22
> **levchv said:**
> Thanks. But I decided remove that packages and virtual box was abled to install.

you removed what ?

And for best support you should run the latest vbox version, not the one in the repos

---

