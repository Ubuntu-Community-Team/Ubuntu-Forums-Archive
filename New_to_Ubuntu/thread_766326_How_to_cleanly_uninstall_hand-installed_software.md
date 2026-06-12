---
title: "How to cleanly uninstall hand-installed software?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by lemmyc on 2008-04-25
Hi all,
I have a few software packages I have installed by downloading tars, configuring, making and installing. They don't appear in Synaptic. How do I cleanly uninstall them?
Example: Alephone installs files to /usr/local/share/Alephone, and puts an executable in /usr/local/bin. Should I just delete these files or will that leave other bits and pieces behind? 
Thanks.

---

### Post by apienk01 on 2008-04-25
If you still have the original source tree where you did the compilation, just cd to it and type:
```
sudo make uninstall
```
If you don't have it anymore, you can try downloading the source again, compiling, sudo make install, and then sudo make uninstall.

---

### Post by kpkeerthi on 2008-04-25
As a side note, you may want to use checkinstall, so you can uninstall the packages using synaptic/apt-get/aptitude.

[https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall)
[http://ubuntuforums.org/archive/index.php/t-2356.html](http://ubuntuforums.org/archive/index.php/t-2356.html)

---

### Post by lemmyc on 2008-04-25
Thanks, that's the info I was after. :)

---

