---
title: "Can't read my Windows 8.1 partition"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by poscomp on 2014-09-14
I just setup a new computer that came with Windows 8.1 64 bit. It would not let me load Ubuntu alongside it. After many tries an recovery of the Windows 8.1 partition I gave up and bought Windows 8.2 32 bit. I installed the windows first and since I could not load Ubuntu 14.04 I loaded 13.10. It installed fine and the grub loaded and I saw and did read/write to all partitions. After I upgraded to 14.04 both OS's run fine but I can't see the Windows partition when I am in Ubuntu. No hardware changed but I can no longer see the partition. Why? Can someone please help me.

Did some work in windows, then went back to ubuntu and it saw and wrote to the windows partition.

---

### Post by Elfy on 2014-09-14
I would stop using it, boot a live session, check that you've still got ntfs partitions and haven't been affected by [lpbug]1265192[/lpbug]

---

### Post by grahammechanical on 2014-09-14
What do you mean, "cannot see the windows partition?" Does an icon for that partition not appear in the Launcher? Does File Manager not list the partition under devices? 

File Manager will not be able to open a Windows 8 partition if Windows 8 is in a state of hibernation and when we shut down Windows 8 it does not shut down. It only hibernates. That is how Microsoft reduces the loading time of Windows 8.

Does the Disks utility show the partition?

Regards.

---

