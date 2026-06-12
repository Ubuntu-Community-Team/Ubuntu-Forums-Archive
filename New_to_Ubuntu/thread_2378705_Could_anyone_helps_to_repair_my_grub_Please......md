---
title: "Could anyone helps to repair my grub? Please....."
date: 2017-11-26
forum: New to Ubuntu
---

### Post by iceanthony on 2017-11-26
Hi...

I got an old notebook.
One or two years age, I replace the original OS from XP to Win10.
Few month later, I clean some partition and install Ubuntu in it, and become a dual OS computer.
Two or three days ago, when I use Win10 to do some office work, the system automatic update and restart.
After restart, It shows "error: unknown filesystem", "Entering rescue mode...", "grub rescue>"

I've google a little, and found Boot-Repair.
And I use a USB stick with ubuntu live CD to boot up my NB, and install Boot-Repair
Here is the BootInfo url below:
[http://paste.ubuntu.com/26042980/](http://paste.ubuntu.com/26042980/)

For your reference, I've try to enter some command in grub shell below:
grub rescue> ls
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)
grub rescue> ls (hd0,msdos7)
(hd0,msdos7): Filesystem is unknown.
grub rescue> ls (hd0,msdos6)
(hd0,msdos6): Filesystem is ext2.
grub rescue> ls (hd0,msdos5)
(hd0,msdos5): Filesystem is unknown.
grub rescue> ls (hd0,msdos3)
(hd0,msdos3): Filesystem is unknown.
grub rescue> ls (hd0,msdos2)
(hd0,msdos2): Filesystem is unknown.
grub rescue> ls (hd0,msdos1)
(hd0,msdos1): Filesystem is unknown.
grub rescue> set
cmdpath=(hd0)
prefix=(hd0,msdos7)/boot/grub
root=hd0,msdos7

if anyone could help?? please.....
if there is any infomation I can deliver, please let me know.
I will response as soon as possible.
Thank you so so so much !!!

---

### Post by iceanthony on 2017-11-26
Thanks for watching...

I've google more and more information, I decide to try myself.
I think that since grub recognize only my (hd0,msdos6), maybe it is the partition where ubuntu is.
And I find a video in Youtube, [https://www.youtube.com/watch?v=yTp4t82SKPU](https://www.youtube.com/watch?v=yTp4t82SKPU)
Follow the step, and problem solved. !!

Thanks again!!

---

### Post by oldfred on 2017-11-26
boot-Repair showed grub trying to boot from sda7 which is your swap partition.
Install is in sda6, and Boot-Repair would just reinstall grub into MBR with correct partition.

But Boot-Repair also pointed out your entire sdb is SFS or dynamic partitions.
That does not even always work well with Windows. Better to convert back to basic partitions.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

