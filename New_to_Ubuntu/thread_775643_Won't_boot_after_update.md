---
title: "Won't boot after update"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Kidder63 on 2008-04-30
Hey folks,

I'm pretty new to Ubuntu and need some advice.  I just installed Ubuntu 7.1 i386 on an old Pentium 3 system I had laying around.  Everything went great with the install, flawless even!  After the OS install I ran the updates which included a new kernel.

Now the system won't boot.  GRUB shows two different kernel versions.  I can select to boot from the 2.6.22-14 kernel and it works just fine.  However, by default the system wants to boot from the new kernel (I don't recall the version, but I can reboot and look if needed).

How can I recover the new kernel version, delete the new kernel version, or change the default kernel to be booted by GRUB?

Any help is most appreciated!!!

Tom

---

### Post by cmnorton on 2008-04-30
Select the grub boot menu. I believe you press the ESC key to do this. 

If you have a recovery option, select that. If you don't, you'll need to use a live CD or Knoppix.

Then go into /boot/grub/menu.lst with an editor and set the default number. Mine's set to 0. 

You could also look at this:

[http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html](http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html)

---

