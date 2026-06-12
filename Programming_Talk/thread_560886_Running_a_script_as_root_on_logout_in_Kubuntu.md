---
title: "Running a script as root on logout in Kubuntu"
date: 2007-09-26
forum: Programming Talk
---

### Post by musther on 2007-09-26
When using GDM, a script can be run (as root) on user logout by calling it from:
/etc/X11/gdm/PostSession/Default

That's great, but now I'm looking for a way to effectively do the same thing from KDM (ie in kubuntu).  It has to be run while X is still up so that it can prompt the user with xdiag, zenity or something.

It can't be run in the background either, it's no good if the prompt appears, but the machine continues to go down before the user has had a chance to act on it.

Thanks.

---

