---
title: "Can't install libgl1-mesa-glx:i386"
date: 2013-03-05
forum: Programming Talk
---

### Post by wgpenney on 2013-03-05
I trying to setup my machine for development of Ubuntu Touch and I've ran into a problem install one of the needed libraries. When I issue "sudo apt-get install libgl1-mesa-glx:i386" I get the following message:


The following packages have unmet dependencies:
libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 8.0.4-0ubuntu0.4)
Recommends: libgl1-mesa-dri:i386 (>= 7.2) 


So the logical thing to do is "sudo apt-get install libgl1-mesa-dri:i386", however then get the following message:


The following packages will be REMOVED:
libgl1-mesa-dri-lts-quantal libxatracker1-lts-quantal ubuntu-desktop xorg
xserver-xorg-lts-quantal xserver-xorg-video-all-lts-quantal
xserver-xorg-video-vmware-lts-quantal
The following NEW packages will be installed:
libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386
libexpat1:i386 libffi6:i386 libgl1-mesa-dri:i386 libllvm3.0:i386
libpciaccess0:i386 libstdc++6:i386


My concern is the packages it's going to REMOVED. Seems to me that if I allow the removal I loose my desktop environment.
I've installed the other required i386 libs without a problem.


Anybody have any thoughts on this?

---

### Post by jayceebee23 on 2013-04-06
I am having the same issue right now. If I go ahead and install the dependent package, I can confirm that it does indeed breaks the desktop environment (most likely due to the removal of ubuntu-destop). I have to go back to a working snapshot to regain my desktop access. I have Ubuntu 12.04.02 LTS running in VirtualBox 4.2.10. Was setting this environment up as a dedicated Android build box.

Thanks in advance.

---

### Post by schragge on 2013-04-06
I guess you are running a 64-bit system (amd64) and some application pulls a whole bunch of 32-bit libraries. See [post=12587000]this post[/post].

---

### Post by jayceebee23 on 2013-04-07
After trying a bunch of things from the above mentioned post, I gave up trying. Created a new box and installed 12.04.1 instead. Did the usual update to pull latest and installed guest additions. Issued the same apt-get packages that was causing me issues. This tine it worked end-to-end. Was able to initialize and sync github repo and a full build. All is well with 12.04.1, the same procedure just don't work with 12.04.2.

---

