---
title: "Compiling GAIM, and plugin woes. D:"
date: 2007-02-22
forum: Packaging and Compiling Programs
---

### Post by Velotix on 2007-02-22
Apologies if this is in the wrong place, but for the most part I don't think it is.

After yet another crash from GAIM trying to send a file and/or direct connect on AIM, I figured "enough's enough, why am I still using Edgy's old beta?" and started looking for a GAIM 2 Beta 6 .deb package. And that's where the problems began.

*The first problem: this version is most definitely newer than the beta 3 in the Ubuntu repositories. So why is Adept Updater telling me that GAIM requires an upgrade? D:*

Fortunately, though, after having to compile the program twice to add SSL support the second time round ( D: ) the new version of GAIM does actually run. However, in doing so, it broke two programs: nautilus-sendto and guifications. The first isn't really a problem because I use KDE most of the time, but the second is a GAIM plugin that I use constantly.

[http://gaim.guifications.org/trac/wiki/Guifications](http://gaim.guifications.org/trac/wiki/Guifications) <--- Just my luck, here's the problem; it needs an upgraded GTK+ runtime to be fixed. That and I need a new version anyway. So I download the tarball, and run into a brick wall. I'm not sure what to do with the unpacked tarball because it's not source code. It seems to contain an install script, but I'm not quite sure how to use it; it's a filetype I've never seen before.

[The file I downloaded is here, so you can see what I'm seeing.](http://downloads.sourceforge.net/gaim/gtk-2.10.8-rev-a-installer.tar.gz?modtime=1170196415&big_mirror=1)

Once this is done, I'll be able to continue using these programs, but I can't shake the feeling of   doing sloppy work on these .deb files, so:

1) How exactly do I do this GTK+ upgrade?
2) How do I make .deb files that don't screw up the auto-update feature?
3) How do I make the .deb files show and check for the correct dependencies, and **what** are those dependencies? (In guifications' case it obviously requires GAIM and GTK 2.10.8, but I'm not sure what GAIM requires.)
4) I assume once a program has been compiled with make, you don't have to re-do the compilation unless you're changing the program. Consequently, because I'm also trying to make .deb packages (to save other people this nightmare), I don't have to keep recompiling the program to remake the .deb packages. Is this correct?

If only this were simple. :P

**UPDATE:** I didn't realise that Ubuntu uses v2.10.6 of the GTK+ runtime, so the problem is null and void anyway. But, my questions still stand. Can no-one help me here? :(

Beta 6 is much more efficient, incidentally - it now connects to MSN much quicker and the design of the buddy list is a little more convenient than before; elements have been resized slightly so they're now less garish and you can now see your own buddy icon at the bottom of the list and edit it just by clicking on it. Extremely useful feature. ^^

Not sure if it improves performance in AIM just yet, though.

---

