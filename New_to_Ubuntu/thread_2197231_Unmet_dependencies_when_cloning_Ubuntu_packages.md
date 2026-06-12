---
title: "Unmet dependencies when cloning Ubuntu packages"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by cashmank on 2014-01-02
Hi there,

I recently followed a path similar to this [http://www.distrogeeks.com/clone-ubuntu-packages/](http://www.distrogeeks.com/clone-ubuntu-packages/) to install the same packages across my two ubuntu installations. I'm getting unmet dependencies warnings when trying to install anything.

For example, when trying to install VLC via the Software Center (which wasn't installed before even though it should have been) I get the "Package dependencies cannot be resolved" error with the following list:

vlc: Depends: vlc-nox (= 2.0.8-0ubuntu0.12.04.1) but 2.0.8-0ubuntu0.12.04.1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.9ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.9ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.5 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.5 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.5 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed


This isn't a VLC-specific issue; other packages are having similar errors. I've checked and at least some of the packages that VLC depends on are already installed.

Any help getting out of this mess would be appreciated!

---

### Post by ibjsb4 on 2014-01-03
Your link is down  :(

What I use to copy my package list:

[http://ubuntuforums.org/showthread.php?t=1028668&p=6482376#post6482376](http://ubuntuforums.org/showthread.php?t=1028668&p=6482376#post6482376)

[http://ubuntuforums.org/showthread.php?t=1636261&p=10194918#post10194918](http://ubuntuforums.org/showthread.php?t=1636261&p=10194918#post10194918)

But I usually use Synaptic Package Manager to create such backup.

[http://ubuntuforums.org/showthread.php?t=2147845](http://ubuntuforums.org/showthread.php?t=2147845)

---

