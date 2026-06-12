---
title: "Changing the name of the kernel"
date: 2010-04-11
forum: Packaging and Compiling Programs
---

### Post by oram.ryan on 2010-04-11
I am currently a maintainer of a Linux distribution based on Ubuntu called infinityOS.  Some of my users have asked if I could change the name of the kernel that the local Grub and other Grub installations identify infinityOS with.

How would I go about changing this?

Thanks,
Ryan

PS You can check out my distribution at: [http://infinityos.net](http://infinityos.net)

-----

I realize that it seems awkward for a distro maintainer to ask how to do this. The truth is the Ubuntu kernels up to now have done everything I have needed, so I never saw the need. I would prefer not to compile a kernel from scratch if possible, as I'm afraid this would introduce bugs. If there is anyway I could use the default Ubuntu configuration, with the exception of the name, I will gladly take that.

I will be building a LFS build this summer for exploration, but would like to avoid as much exploration as possible at this point (I had lots of exploration two months ago, now I'm mostly wrapping up) with my production distro as I have quite a few users at this point.

---

### Post by oram.ryan on 2010-04-12
So it seems like Linux Mint uses the Ubuntu Kernel packages, but has it listed under a different name in Grub. I'll going to see what they did and blatantly copy it.

---

### Post by SevenMachines on 2010-04-12
I might be mistaken but are you looking to rename grub menu entries? if you're using grub2 you might want to look at /etc/grub.d/10_linux (from grub-common), this auto-detects and generates linux entries, i think linux_entry() deals with the actual name.
You used to be able to add a custom script in /etc/grub.d/ which could go through /boot/grub/grub.cfg.new and rename anything you liked before it become grub.cfg proper. I haven't checked if this still works though

[EDIT] Just checked quickly and a grub.d script that 'sed' renames entries in grub.cfg.new still works fine

---

