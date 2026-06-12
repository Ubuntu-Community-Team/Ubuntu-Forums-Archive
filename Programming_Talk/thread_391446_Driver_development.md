---
title: "Driver development"
date: 2007-03-23
forum: Programming Talk
---

### Post by Mathiasdm on 2007-03-23
I've been wanting to get into driver development for some time (the Broadcom drivers, to be precise), to test the latest driver version, and perhaps even help look for bugs.

The thing is, doing this requires recompiling the kernel. I've already done so, and it's not so hard, but how does one deal with the 'cruft' generated?
For example:
-The Grub menu contains a list with every kernel version installed on my machine. Is there a way to get rid of this? (Or, perhaps, get rid of some of the installed kernels -- the ones I choose).
-Some programs, like VMWare player/server, need to be recompiled to work on the new kernel. Are there any easy ways to take care of such things? (I'm afraid I don't know any scripting languages -- C, Java and Assembly are all I know as of this moment.)

---

### Post by j_g on 2007-03-23
I can answer one query in your post.

To modify the list of operating systems that are presented when your computer boots, open a terminal window and type:

sudo gedit /boot/grub/menu.lst

This will load a Grub configuration (ie, text) file into a text editor. This file contains information about all the operating systems that Grub can boot into. Edit this text file to remove those ones you don't want, and resave the file.

For example, here's some text that appears in my menu.lst, which allows booting into Ubuntu and doing a memtest:

```
title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot
```

Grub displays this as the "Ubuntu, memtest86+" option when my computer boots up. If I want to remove this item from the boot menu, I'd just delete the above lines, and resave this newly edited menu.lst.

NOTE: You can also change the order of the items in the boot menu, and change which one is the default item, by editing the contents of menu.lst.

---

