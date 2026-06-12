---
title: "Switch from Dual Boot to Ubuntu Exclusive (Messed up?)"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by sidka on 2008-10-02
Computer: Compaq Presariov2000
Original OS: Windows XP Home
New OS: Ubuntu (Hardy Heron)

First off, I'm going to admit I'm not the brightest when it comes to computers and I should have asked for clarification beforehand, but now that it's like this, I'm not sure what to do. Please help?

I sucessfully dual-booted Ubuntu and XP about a week ago and decided to make the switch permanently without losing my data. I read through the forum archives and thought I understood what to do. So I used the installation disk and installed over Windows XP. This created a new instance of Ubuntu on my machine and it will only boot straight to that without providing a chance to atleast go to the version I had before, which would at least see the Windows partition.

I would have left it alone in the first place, but my laptop only has 70GB of space and splitting it 50-50 made me feel a little cramped for space.

Now the version of Ubuntu I had before has all my files and I can't figure out how to get to it. Again, any and all help would be appreciated, and if you could direct me as to how I might be able to get to the older version, I may be able to figure it out from there.

Once again, I would really appreciate any and all advice in this situation. I can provide more information if requested, but I am using my roommate's computer right now, as I have yet to install the drivers for the wireless internet my laptop uses. Thanks again.

---

### Post by bumanie on 2008-10-02
boot live ubuntu cd and post the output of terminal command > sudo fdisk -l that's a lower case L

---

### Post by Kuroyume on 2008-10-02
pushing Esc right after the BIOS screen, but before the ubuntu progress bar should bring up the boot menu, which will show your installed OSes

---

### Post by sidka on 2008-10-02
> **bumanie said:**
> boot live ubuntu cd and post the output of terminal command that's a lower case L

Disk /dev/hda: 80.0GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

Device Boot  Start  End  Blocks  Id  System
/dev/hda1 *  1  9494  7620253+  83  Linux
/dev/hda2  9495  9729  1887637+  5  Extended
/dev/hda5  9495  9729  1887686  82  Linux Swap / Solaris

---

