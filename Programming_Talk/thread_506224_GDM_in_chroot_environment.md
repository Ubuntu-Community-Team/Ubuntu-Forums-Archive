---
title: "GDM in chroot environment"
date: 2007-07-21
forum: Programming Talk
---

### Post by Joshua Hesketh on 2007-07-21
Hello,

I am working on a patch for reconstructor that lets you log into a live CD and make changes before burning it.

The way this works is that reconstructor (or live CD's in general) extract the live CD's file system. These files can then be modified, put back together and then placed back on the CD.

This is all well and fine, and it is actually easy enough to start a GDM session from a chroot environment. I achieve this by copying over my resolv.conf file and starting dbus and then gdm (which opens a new session on TTY9 [F9]). However because of the way live cd users are created I can't log in easily or set up user permissions... Put simply, I run into a lot of problems with users.

If somebody could show me how to use GDM in a chroot environment properally that would be very much appreciated... If not, does anybody know where I might find good documentation on how live cd users are created?

Thanks heaps,
Josh

P.S [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) has good information but the part about starting gnome does not work due to users permissions and whatnot.

P.P.S If there is a better place (on ubuntuforums or otherwise) to be asking this sort of question, please let me know.

---

### Post by Joshua Hesketh on 2007-07-29
Does anybody have any clues or suggestions? Perhaps I should be posting this somewhere else?

---

