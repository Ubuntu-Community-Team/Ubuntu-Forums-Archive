---
title: "FreeDOS and Win98 on same fat32 partition?"
date: 2007-08-14
forum: Other OS Talk
---

### Post by the_darkside_986 on 2007-08-14
I am trying to figure out how to make this work. I installed Windows 98 SE on a fat32 primary partition, and it worked. Then I installed FreeDOS on the same partition, and it also worked but the boot menu did not give me the option of booting Windows 98. I am trying to figure out what file(s) should be edited so that Windows will appear as an option when starting FreeDOS. (Windows 98's MS-DOS is the only thing  that can play TES:Arena on the old machine but it doesn't play other DOS games too well like FreeDOS does.)

There is no point in trying to use Grub because the entry for FreeDOS and Windows will always be the same if they are on the same partition.

---

### Post by Frak on 2007-08-15
If you selected the partition that you installed Windows 98 on, you've unfortunately overwritten Windows 98.
As two OS's can't exist on the same partition unless virtualization is present.

---

