---
title: "Boot Manager missing after installing Ubuntu 12.04 beside Win-7"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by vinitrg on 2012-06-22
I used the windows installer of ubuntu 12.04 to download and install Ubuntu. I remember installing Ubuntu in different drive than that which contains Windows-7, it asked me to restart and when I did, the boot manager was missing. Can anyone understand what could have happened here?

---

### Post by anewguy on 2012-06-22
Since nobody has answered, let me give this a shot:

If you have 2 physical disks - let's say disk 1 and disk 2.  If disk1 is where Windows is installed, and you installed Ubuntu to disk2, and if the only thing that happens is that you still boot straight into Windows, then I know your problem.

When you install Ubuntu, you are given the option of where to put the boot manager.  I believe by default it is the same disk you are installing Ubuntu to.  So in your case, everything, including the boot record, etc., for Ubuntu is on disk2 - it never touched disk1.

If you'd like to test this, restart your PC, go into the BIOS settings and change the boot device to your second drive.  Some motherboards' BIOS let you actually do this without changing the BIOS settings - there may be a key you can press that brings up a menu where you can select where to boot from.  I believe that once you boot from that drive you will see Ubuntu.

So, if you make it that far, someone can probably tell you how to change it in your existing installation.  However, since this is a brand new install, you might find it easier just to re-install, changing the device the boot record is installed to.  Please see [this]("https://help.ubuntu.com/community/Grub2/Installing") for some simple instructions with screen shots to show you how to do this.

---

