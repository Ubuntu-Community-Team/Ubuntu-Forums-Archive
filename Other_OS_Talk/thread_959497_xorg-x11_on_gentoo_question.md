---
title: "xorg-x11 on gentoo question"
date: 2008-10-26
forum: Other OS Talk
---

### Post by fontenot_1031 on 2008-10-26
I'm following the gentoo.org documentation to install xorg but when I emerged xorg-x11 I forgot to change my use flags to have INPUT_DEVICES="keyboard mouse" and VIDEO_CARDS="radeon". Whenever I emerge -C xorg-x11 it only unmerges the x11 base but I want to remove all of it's dependencies (all 138 that were emerged when I first typed emerge xorg-x11)(also emerge -av --depclean xorg-x11 doesn't remove all of them either). I guess my first question is do I even need to unmerge all of them, if I do then does anyone know how to remove all of the dependencies of xorg?
Thanks in advance.

---

### Post by handy on 2008-10-26
Have a look at the Portage documentation, which is (as is all of the Gentoo documentation) an excellent resource:

***_[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=1)_***

Please don't consider this a RTFM, I would tell you the answer if I knew it. :-)

---

