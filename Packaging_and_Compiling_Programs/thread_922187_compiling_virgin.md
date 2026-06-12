---
title: "compiling virgin"
date: 2008-09-17
forum: Packaging and Compiling Programs
---

### Post by uvdevnull on 2008-09-17
Hope I'm posting in the right section, please redirect me if not so...

Before I start, would like to say that I'm a noob to Linux in general, not to mention compiling code.  However, I do enjoy learning by doing and I came across a problem I'd like to solve, hence my need to do the following:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/187540/comments/7](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/187540/comments/7)

I've downloaded source files for both packages and the patches.  I've patched the gnome-panel code successfully and ran debuild, apparently compiling this thing.  Bunch of stuff scrolled up the screen for a few minutes and then finished.  Not entirely sure if it was 100% successful but let's assume so for the time being...

I get stuck with patching libwnck because the patch is for version 2.22.1 while I have 2.22.3.

I tried changing the version number within the patch but I'm pretty sure it should not be done like that.  Although the first patch succeeded, the second (changelog) did not:

```

patching file libwnck-2.22.3/ChangeLog
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file libwnck-2.22.3/ChangeLog.rej

```

Do I even need to worry about the ChangeLog?  If the main code patched successfully without error, is it safe to compile and run?

Not sure how to proceed, would appreciate a little guidance.

Thanks guys,
uvdevnull

---

### Post by InfinityCircuit on 2008-09-17
The changelog is not used in compilation, so it shouldn't be a problem that the patch didn't apply correctly to that file.  You can either use a text editor to compare changelog.rej with changelog, if you're curious, or use a program like Kompare that will do it for you.

---

### Post by uvdevnull on 2008-09-17
Thanks.

Ok, so I ran the final command on that list:
```
sudo dpkg -i *.deb
```
Again, a bunch of stuff scrolled up the screen and it was done.
However, the bug did not go away after a reboot and I'm not sure if I'm done yet.  How can I tell if the patched code was compiled and applied (replaced) the previous version?
Like a dumbass, I didn't save the output of dpkg but it did say something about replacing gnome-panel-something with gnome-panel-anotherthing.

Sorry, I do realize how goofy this is sounding, but this is what noobs do, no? :)

---

