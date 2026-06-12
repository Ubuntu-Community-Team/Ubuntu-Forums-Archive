---
title: "Ubuntu wubi how much of Windows is running when logging into Ubuntu"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by Sherman_Willden on 2014-05-06
I installed Ubuntu side-by-side with Windows 7. How much of Windows is running when I log into Ubuntu during the boot process? Is it all Ubuntu? If I want only Ubuntu running do I need to reinstall and install Ubuntu only?

Thank you;

---

### Post by oldfred on 2014-05-06
Wubi uses the Windows boot loader to start and is a image in a large file root.disk inside the NTFS partition. Windows is not running. But wubi is taking up space in the NTFS partition up to a max of 30GB.

If you only want Ubuntu on system you have to install into a separate partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: > Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


---

### Post by Sherman_Willden on 2014-05-07
Thank you

Sherman

---

