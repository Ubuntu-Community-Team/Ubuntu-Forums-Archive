---
title: "Reboots at progress bar, and cant finish installing"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by mortega816 on 2008-08-21
Hi, I have a problem and was hoping someone here could help me out. I recently installed ubuntu within windows xp pro. But when I get to the progress bar after rebooting and choosing to boot to ubuntu, my dell monitor displays a "entering power save" and reboots, hence Im unable to boot into ubuntu. There is no way to disable it in the bios that I could find. Any help on disabling this power save would be greatly appreciated.

---

### Post by gobbles414 on 2008-08-21
So you're saying that you installed Ubuntu from Windows using Wubi (or something similar), and now Ubuntu won't load correctly? What are your computer's specs? You may want to consider making a true dual-boot system, or running Ubuntu in a Windows-based virtual machine.

The advantages of dual-boot are that Ubuntu will run faster and it will recognize most/all of your computer's hardware. The disadvantage is that for most reliable performance, you'll need to: backup all of your data, reformat your hard drive and partition it using a Windows installation disk, reinstall Windows on one partition, and then install Ubuntu on the other partition.

I like the *VirtualBox* virtual machine, which can be downloaded from [here]("http://www.virtualbox.org/"). One advantage of virtualization is that you don't have to reinstall Windows. Another advantage is that Ubuntu will almost certainly boot. The main disadvantages of virtualization are that some hardware might not work (e.g. webcam) and Ubuntu will run more slowly than in a dual-boot configuration.

Does any of this help?

---

