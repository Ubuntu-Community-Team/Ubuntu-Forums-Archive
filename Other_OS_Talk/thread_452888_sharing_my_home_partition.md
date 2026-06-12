---
title: "sharing my /home partition"
date: 2007-05-23
forum: Other OS Talk
---

### Post by tchoklat on 2007-05-23
I have various distros on my system including XP (which does not have an internet connection by the way!).

Ubuntu has a separate /home partition, the other distros have their home in the same partition as the program is installed. Bootloader is the Ubuntu one with the other distros chainloaded!

I have set up Thunderbird and Firefox to share profiles on a separate Fat32 partition and all is kool. I want to share my Ubuntu home partition with the other distros; SamLinux, Fedora, PCLinuxOS and SL; and move all the 'goods on the respective /home directories to this shared /home partition.

Can I do it and if so how? - I am not an advanced terminal user!

tchoklat

---

### Post by Pobega on 2007-05-23
Well, you'll most likely need to add a line in /etc/fstab for the /home partition. Check Ubuntu's /etc/fstab for an example, and hell, you can actually copy/paste that line if you want to.

As for Fat32 Firefox/Thunderbird from Windows, I have no idea. I've never done that before. But I imagine you can do some sort of a symlink using the *ln* command.

---

