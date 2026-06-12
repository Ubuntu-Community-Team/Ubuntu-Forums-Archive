---
title: "Some machines refuse to dual-boot"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by japhyr on 2011-11-02
I have a batch of 10 laptops that are identical.  They were all running Windows 7.  I tried to install 11.04 alongside Windows 7, and it worked on 7 of the 10 machines.  Three of the machines refused to dual-boot, only offering to replace Windows with Ubuntu.

Is there a straightforward reason that some machines would refuse to dual-boot?

---

### Post by dolphin194 on 2011-11-02
On the Ubuntu installer, have you tried to edit the partitions manually?

---

### Post by mike555 on 2011-11-02
Do they already have 4 primary partitions?

---

### Post by Mark Phelps on 2011-11-02
> **japhyr said:**
> Is there a straightforward reason that some machines would refuse to dual-boot?

If by "identical" you mean even down to the hard drives and partitioning of the same -- then there is no straightforward reason for only SOME of them to fail.

You should check the failing ones to see what partitions are on the drives.

---

### Post by redsariku on 2012-02-14
On certain laptops Windows places the file management files near the end of the hard drive and will not allow those files to be moved no matter how many times you do drive optimizations. Ubuntu cannot remove those files so it wipes them off the hard drive unintentionally. This only happens on certain laptops that come with Windows pre-installed. I don't know if it is the manufacturer or the installer that can somehow do this but I have had the trouble with IBM (Lenovo) thinkpads and the Acer 10.1 in and HP minis. Most of the time defragmenting the hard drive twice will move those files then they are not a problem. Grub recognizes the system but you won't be able to pull it up with out the file managers.

---

