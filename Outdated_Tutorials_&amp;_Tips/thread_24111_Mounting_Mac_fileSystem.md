---
title: "Mounting Mac fileSystem"
date: 2005-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by fallenone on 2005-04-05
I am currently having some trouble, a friend of mine's bowerbook died and can no long log in at all and has done a backup but didn't get a few files and i want to use ubuntu to get those files, and i know how you generally mount things  in linux such as : mount -t hfs+ /dev/hda /mnt/mac1  

but when i do it says unknown file system, so it doesn't recognize it, do i need to recompile the kernel and make my own cd or? is there another filesystem i should try using? im not a complete newbie at linux but i have never recompiled the kernel to include such things so if any one could point me in the correct direction as to how to mount a powermac g4's hd so i can pull those files off?

any help would be MUCH APPRECIATED!!

---

### Post by tormod on 2005-04-05
[QUOTE=fallenone]i know how you generally mount things  in linux such as : mount -t hfs+ /dev/hda /mnt/mac1  

but when i do it says unknown file system, so it doesn't recognize it, [/QUOTE]

For one thing, the file system type is "hfsplus" and not "hfs+". You can (as root) do
**modprobe hfsplus** and then **cat /proc/filesystems** to see if your kernel has
support for hfsplus.

HTH,
Tormod

---

### Post by fallenone on 2005-04-05
yeah thanks i finally figure out it was hfsplus after playin with it thanks!

---

