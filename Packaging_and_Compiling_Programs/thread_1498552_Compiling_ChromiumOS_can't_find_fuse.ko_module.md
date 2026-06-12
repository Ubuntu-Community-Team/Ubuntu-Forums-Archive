---
title: "Compiling ChromiumOS can't find fuse.ko module"
date: 2010-05-31
forum: Packaging and Compiling Programs
---

### Post by NMuench on 2010-05-31
First of all, I don't know if this is the right place to post this so, if it should be somewhere else, move it. And I'm using the Ubuntu forums instead of the Chromium forums because this is an Ubuntu-related problem.

Now to the question, I've been searching everywhere for an answer without success, searching the Chromium forum has been a shot in the dark, and this forum is my last hope. I'll go as deep as possible to explain this.

I've attempting to compile ChromiumOS (for 32-bit/x86) on Ubuntu 10.04 64-bit (running within VMware Workstation 7.1), and I get to the part where I run the script to enter chroot. This is what I get after running it (after the part where I login):
```
Mounting chroot environment.
Not mounting chrome source
Mounting depot_tools
-- Note: modprobe fuse failed.  gmergefs will not work
```
I have the following folders within the [chromiumos] folder: chromiumos.git, cros_deps, src

I know that I have to have a file called "fuse.ko" in the "/lib/modules/2.6.32-22-generic/kernel/fs/fuse" folder, all that's in that folder is "cuse.ko"

I've had no luck compiling fuse itself (I get errors during make phase), I'm compiling it using the out of date info I've found through google.  One thing I've noticed is that within the fuse folder, the kernel folder is gone beginning with version 2.8.0.  And I'm guessing that Karmic (9.10) had that fuse.ko file, since it use fuse 2.7.4 (compared to Lucid's 2.8.1).

I know Fedora 13 has that fuse.ko file, but I'm not sure which version of fuse they are using.

I know this is a lot, **I'll take questions to clear up any confusion**, I just want some up to date information dealing specifically with Lucid.  And yes, I'm using latest info from the ChromiumOS Developer site.

Thanks, progress in the solving this issue would be extremely useful.

---

