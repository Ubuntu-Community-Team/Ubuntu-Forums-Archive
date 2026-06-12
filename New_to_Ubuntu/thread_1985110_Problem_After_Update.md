---
title: "Problem After Update"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by DGINSD on 2012-05-22
Update manager launched before I left for work this morning, so I clicked install and left, but apparently all did not go well, the kernel upgrade seemed to cause problems or something. If I install or remove anything now I get this...

[IMG]http://s19.postimage.org/ry5tegt3n/Screenshot_from_2012_05_22_18_01_55.png[/IMG] 

Here's the bottom part of the detail box from synaptic

```
/usr/sbin/grub-mkconfig: 39: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.2.0-24-generic

```

If I try to update-grub I get almost the same message, trying to open grub customizer will produce the same error as well.

Help I'm lost???

---

### Post by DGINSD on 2012-05-28
Still have no clue as to the cause of this issue, but thought I should share the solution in the interest of helping others, and to share my discovery of a nice little piece of software every non linux guru should have in his bag of tricks.

The solution was the purgeing and reinstallation of grub and what I used to do this was found here [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

I chose the live CD method, and at first tried to just re-install, but I still had the same problem after that, so I decided to try the advanced options and have grub purged prior to re-installation. This option will give you a list of commands to execute and and instructions to follow after. Worked like a charm, and repaired my issue, whatever it actually was.

---

