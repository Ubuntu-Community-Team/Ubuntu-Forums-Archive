---
title: "Windows 8.1 and Ubuntu"
date: 2014-12-19
forum: New to Ubuntu
---

### Post by Mark de J on 2014-12-19
Hello,

I'm going to re-install my system and want make a dual boot, but can I put it both on a other partition and how?

I am going to install **Windows first**, is that okay?

---

### Post by pixel2 on 2014-12-19
of course you can install dual boot (Ubuntu + Windows 8 (or whichever)) but do it wisely..... Ubuntu first (due to [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)). After installing both systems, dont forget to rebuild your bootmenu (its always good to do it from within Windows). Than you should be good to go.

---

### Post by Mark de J on 2014-12-19
Yeah, I will try what I can do.

---

### Post by oldfred on 2014-12-19
Is this newer hardware that has both UEFI and BIOS boot modes.
If so, you just need to be sure to install both systems in the same boot mode, or both UEFI or both BIOS.
If older hardware, then BIOS should be only choice.

In both cases, generally better to install Windows first, then use Windows disk tools to shrink the Windows NTFS partition. Then immediately reboot Windows so it can run chkdsk and update to its new size. Make sure fast boot or always on hibernation is off. Windows likes to reset to its preferred defaults. If UEFI usually better to have secure boot off.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

UEFI installs make it a bit more complex as you have the added settings in UEFI/BIOS that you must make first.
If you need info on UEFI, many links in the link in my signature.

---

### Post by Mark Phelps on 2014-12-19
Seeing as how you mentioned Windows 8.1, if this is a new machine, it likely has UEFI -- in which case, you need to read through the material in the link: [http://ubuntuforums.org/showthread.php?t=2147295]("http://ubuntuforums.org/showthread.php?t=2147295")

---

### Post by col48 on 2014-12-19
I think the advice used to be that Windows installed after Ubuntu messed up Ubuntu.  Has that changed with more recent Windows releases?
Or is that advice irrelevant if what you're doing is replacing one Windows copy with another without changing partition structure?

---

### Post by Mark Phelps on 2014-12-19
The only "messing up Ubuntu" that I've run into is that on MBR BIOS machine, installing any Windows version will overwrite the MBR, thus forcing the next boot to be directly into Windows.  That has been fix by reinstalling GRUB such that it overwrites the MBR, restoring boot to Ubuntu.

On UEFI machines, this is an entirely different situation.

---

