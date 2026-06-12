---
title: "Deleting a (possibly unused MBR) ?"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by mahela007 on 2014-01-25
This post is about Gparted and not about Ubuntu in particular. 
Recently, I installed windows 8.1 using UEFI and the GPT partition scheme. However, the hard driver previously had windows 7. 

I tried to resize and create some new partitions using GParted. At first, it seemed to be successful, with GParted showing the modified partition sizes and the new partitions.
 However, when I booted into windows 8.1 and checked the partitions, the partitions had not been changed at all. The new partitions were not visible and the old partition had not been resized. 

What I think happened is that GParted saw the old (and now unused) MBR on the hard drive and determined that the hard drive was using MBR instead of GTP. Therefore, it edited the MBR. Windows is actually using GPT and so the changed to the MBR weren't visible in windows.
So how do I fix this? Should I just delete the MBR ? If so, how can I do that?

---

### Post by oldfred on 2014-01-25
I know when you install Windows in BIOS boot mode with MBR on a previous gpt partitioned drive it leaves the backup gpt partition table.
Normally we do not erase MBR, that can create more issues that it may solve. And never erase partition info in MBR. 

Best to post these.

sudo parted -l
       sudo parted /dev/sda unit s print

 sudo gdisk -l /dev/sda

---

### Post by mahela007 on 2014-01-25
Ok.. I will run those commands and post the output. Meanwhile, I found this link 
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx) that explains that all GPT drives also have something called a "protective MBR" that is used to "protect the drive from legacy software". Maybe that's what Gparted is using?
(Gparted shows 3 partitions on the HD while windows shows only one partition)

---

### Post by oldfred on 2014-01-25
You may be into the hybrid MBR/gpt configuration, which is not recommended? Again we need to see details.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by mahela007 on 2014-01-27
Thanks for the help guys. 

The problem seemed to solve it self. I defragmenteded the hard drive in windows and after one or two reboots, it started showing all the partitions. I also ran the Diskpart command line utility in windows just to list the available partitions. (dunno if that's what fixed the problem)

---

