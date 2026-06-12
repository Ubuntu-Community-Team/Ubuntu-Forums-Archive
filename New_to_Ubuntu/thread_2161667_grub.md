---
title: "grub"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by emmbio on 2013-07-11
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="drm.debug=0xe plymouth:debug"
GRUB_CMDLINE_LINUX="" 

is there anything i should edit?
it seems my computer cant boot in gui

---

### Post by dannyboy79 on 2013-07-11
what is the problem? your grub looks fine to me BUT I also have no idea what symptoms you're experiencing

---

### Post by gifford on 2013-07-11
What version of Ubuntu are you using?
The difference between what you posted and my configuration is:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
I think what you have is for the verbose mode to see what is going on during the boot.

---

