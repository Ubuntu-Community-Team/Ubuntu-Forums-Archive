---
title: "Skip Windows 7 bootloader and go directly to grub"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by dalpi on 2011-10-09
I installed Wubi (Natty Narwhal) on my laptop. When I start the laptop, I have to select ubuntu on the windows 7 bootloader, and then it goes to the grub bootloader, where I have to select ubuntu generic. Is there a way to entirely skip the windows bootloader and go directly to grub?

---

### Post by oldfred on 2011-10-09
Wlecome to the forums.

Not easily with wubi. It may be time to consider a full install.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.




(one of the oldtimers here proved it could be directly booted by putting the wubi root.disk in a separate partition and booting it from the grub2 install in his regular install, but that is very advanced)

---

