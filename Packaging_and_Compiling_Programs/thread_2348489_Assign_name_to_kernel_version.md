---
title: "Assign name to kernel version"
date: 2017-01-04
forum: Packaging and Compiling Programs
---

### Post by muurs on 2017-01-04
Hi guys,

I have made a few minor changes to the Linux kernel and now I want to build it with all the default settings of Ubuntu 14.04.5 LTS (trusty). I followed the instructions from this [_article_]("https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel"). Using this method I can build a kernel with the same default settings as the official distribution, right?

The section "Modifying the configuration" explains how one can assign a name to the new kernel version. I have changed debian.master/changelog to
> 
linux (4.4.0-57.78+test1) xenial; urgency=low
[...]

but this name is not shown in the GRUB menu.

My questions are:
1. What is wrong in the above line?
2. Is there a tool to append to changelog?

---

### Post by mc4man on 2017-01-04
Nothing to do with 17.04 so thread should be moved.
The debian changelog just gives a name to the created packages, nothing more.
Probable that you need to address this during the kernel package build, maybe with an option, replacing red  - 
--append-to-version=-[COLOR="#FF0000"]customkernelname[/COLOR]

---

### Post by howefield on 2017-01-04
Moved to the "*Packaging and Compiling Programs*" forum.

---

