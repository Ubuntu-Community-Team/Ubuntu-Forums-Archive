---
title: "How do I get single patches applied to the Ubuntu kernel?"
date: 2009-09-28
forum: Packaging and Compiling Programs
---

### Post by MacUntu on 2009-09-28
I'm running a custom kernel and the package sreadahead is not working. On its Launchpad page there is a note that sreadahead requires a kernel patch included in the Ubuntu kernel. So where can I get this patch?

**Edit:**
Gnaaa, of course it's in the source package of the source package. :D

apt-get source linux-source-2.6.31 -> linux_2.6.31-11.36.diff.gz

**Edit 2:**
Cheered too soon - the archive contains only a one file diff. :D The working patch can be found at [http://code.google.com/p/sreadahead/](http://code.google.com/p/sreadahead/) but now still I'd like to know how to get _single_ Ubuntu kernel patches?

**Edit 3:**
Above patch doesn't work. Instead I looked up the changes via Ubuntu's kernel git page: [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=commitdiff;h=8cced4c6dcdcc6ba4a679dcf7ebb3000045a581f](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=commitdiff;h=8cced4c6dcdcc6ba4a679dcf7ebb3000045a581f) now everything works and I guess that's the way you track down single patches in the kernel.

---

### Post by Milos_SD on 2009-11-07
Did you find the patch? I need it too for custom kernel.

---

