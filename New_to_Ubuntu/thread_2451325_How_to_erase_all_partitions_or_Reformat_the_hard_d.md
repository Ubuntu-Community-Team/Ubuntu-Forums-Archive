---
title: "How to erase all partitions or Reformat the hard drive?????"
date: 2020-10-01
forum: New to Ubuntu
---

### Post by az64x on 2020-10-01
I am trying to reinstall Lubuntu 20.04 on a PC I have been testing 20.04 with.  I wanted to start with a fresh install.
 

 Many weeks ago it installed 20.04 with no problem, but now it will NOT install again.
 

 I boot on a USB or a DVD and select icon “Install Lubuntu 20.04 LTS” and everything seems fine.
 

 However, it gives an error saying “The installer failed to create a partition table on fdo.”
 

 Apparently it is seeing a partition from first install.

 

 I used KDE partition manager and tried to delete all partitions, but obviously I failed.
 

 **How can I remove all partitions or maybe reformat a hard disk????**?

---

### Post by ajgreeny on 2020-10-01
I suspect fd0 or fdo is a floppy disk; I haven't seen one of those for about 12 years.
Check  the disk your trying to use; does the machine have a floppy disk?

---

### Post by guiverc on 2020-10-02
> **az64x said:**
> I am trying to reinstall Lubuntu 20.04 on a PC ..

 However, it gives an error saying &#8220;The installer failed to create a partition table on fdo.&#8221;
 

If you read the [Lubuntu 20.04 release notes]("https://lubuntu.me/focal-released/") you'll read

> **Calamares Tries to Install a Bootloader to Floppy Drive**

 If a system has a floppy drive with a floppy disk at the time of boot, Calamares [tries to install a bootloader to the floppy]("https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1873128"). If the floppy disk is removed from the drive before boot the installation proceeds without failure.



This is a bug in `calamares`, or the installer used by Lubuntu. It's not trigged if the system has a drive, but if a floppy is inserted in the drive (I discovered in testing after answering a support question where I had to dig out & use old floppies, but forgot to remove them..).

By ejecting the floppy drive before starting `calamares` (ie. *before starting the install*), the installer will ignore the floppy.  That bug was been reported upstream, and it's been fixed for later systems, alas not before 20.04 was released.  That's the only case where I've seen the `fd0` appear.

--

There are a number of cases where after a install failure, KDE Partition Manager will misbehave, the fix is just to reboot & start again.

 Once you have rebooted, you'll discover KDE Partition Manager performs as expected, and the installer can be re-started. I forget the cause of this issue (*it'll be on launchpad somewhere; two bugs for this I believe*), so this advice is more generic (*it's been more than 4 months since I've dealt with that issue on bug reports*).

---

### Post by GhX6GZMB on 2020-10-02
> **az64x said:**
> 
**How can I remove all partitions or maybe reformat a hard disk????**?

When you get the installer running (pending the answers to fd0 above), select "Manual Partitioning" during install. This will allow you to define new partitions and to format them. The Calamares installer does this quite well.

---

### Post by az64x on 2020-10-02
YES, this machine does have a floppy drive.    I have not had a floppy in many years.

**Would it solve the issue if I just remove the floppy drive?????**

---

### Post by guiverc on 2020-10-02
The bug is with `calamares`, or the installer Lubuntu uses. Calamares is getting the hardware from the BIOS of the machine itself (the newer version just ignores any devices starting with `fd`if I remember correctly).

The presence of the floppy drive itself in the system **shouldn't** impact the install, in my experimentation (on two boxes; hp & dell only as most systems don't have floppy drives anymore) not having a floppy in the drive didn't create the issue, **it was a floppy being sensed in the drive** that created the issue (**so a faulty drive that detects a floppy as being inserted even if it's not inserted will cause this issue**).

- *possible workaround*
[B]
If your floppy drive is misbehaving[/B], I'd go into BIOS settings and disable the floppy drive. I tested that and it prevented the issue (hp pentium 4 box running Lubuntu 18.10 & 19.04 being the last x86/32-bit systems, and dell running modern Lubuntu amd64/64-bit system).  This is all from memory, what I did can be found on *launchpad* or *github* if needed (*you don't need i**t; it impacts non-Ubuntu systems too; I may have tested using manjaro for that issue but I forget*)

If you upload your calamares *session.log (I think it's called; found in ~/.cache/calamares/ ; if it's not session.log you'll see it anyway*) I can have a look, but I'm basing this from what you've provided and what I recall from prior issues  (development is all over for *groovy* too now, and *focal* was now two cycles ago)

---

