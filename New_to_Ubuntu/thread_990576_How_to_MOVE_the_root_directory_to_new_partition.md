---
title: "How to MOVE the root directory to new partition?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by sarc on 2008-11-22
Now I'm double booting Windows XP and Hardy... I want to nuke Win, move my Ubuntu root partition to the XinXP partition, and increase the size of my data partition by adding the space of the old root partition.  I could do it with the backup procedures using gzip, but I don't need to zip and unzip... is there a command that lets me just bit-copy one partition to another?  And do I need to change the MBR or can I just edit the Grub boot menu to boot Ubuntu from my C: drive instead of WinXP?  Thanks...

---

### Post by magli on 2008-11-25
I am pretty sure that editing the grub menu will suffice.

As for moving the partition:
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=N2x&q=linux+move+root+partition&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=N2x&q=linux+move+root+partition&btnG=Search)

From your post it sounds like you have three partitions: windows, data and linux root. It would be a lot easier for you to add the windows partition to your data partition, and just leave the linux root as it is (and potentially resize the linux root to your liking.)

---

### Post by go_beep_yourself on 2008-11-25
> **sarc said:**
> Now I'm double booting Windows XP and Hardy... I want to nuke Win, move my Ubuntu root partition to the XinXP partition, and increase the size of my data partition by adding the space of the old root partition.  I could do it with the backup procedures using gzip, but I don't need to zip and unzip... is there a command that lets me just bit-copy one partition to another?  And do I need to change the MBR or can I just edit the Grub boot menu to boot Ubuntu from my C: drive instead of WinXP?  Thanks...

How about using gparted to resize and delete partitions?

---

### Post by go_beep_yourself on 2008-11-25
> **sarc said:**
> is there a command that lets me just bit-copy one partition to another?

Yeah, it's called dd.

[http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Paqman on 2008-11-25
> **go_beep_yourself said:**
> How about using gparted to resize and delete partitions?

+1

You don't need to move the root, just delete the Win partition, expand the other partition(s) and remove the entry in /boot/grub/menu.lst that points to Windows.

Moving and resizing partitions can be quite slow, and it would be wise to take a backup first.

---

### Post by unutbu on 2008-11-25
Moving a root partition is complicated.
Here are some of the problems that will arise if you were to use dd to copy the Linux root partition to a new partition:
[list]
[*]GRUB would have to be reinstalled because the stage1 bootloader code (in the MBR) would be pointing to the wrong partition.
[*]Your /boot/grub/menu.lst would have to be edited because many of the UUIDs would be wrong.
[*]The file /etc/initramfs-tools/conf.d/resume would have to be updated if you want hibernation to work.
[*]Your /etc/fstab would have to be edited (due to UUIDs as well)
[/list]

There are quite likely other things that would need fixing.

It would be much simpler and safer to
[list]
[*]backup your data before resizing any partitions. Besides giving you the freedom to be more daring in your experiments, backing up will allow you to delete partitions and then create new ones as you wish. This is sometimes quicker than using GParted to resize partitions.
[*]then do a fresh install of the operating system.
[/list]

---

### Post by Paqman on 2008-11-25
> **unutbu said:**
> backing up will allow you to delete partitions and then create new ones as you wish. This is sometimes quicker than using GParted to resize partitions.


True. Moving partitions in particular is slooooooooow.

---

### Post by sarc on 2008-11-29
Thanks for answers.  Yes I have several partitions: WinXP, Root, Swap, and Data.  I wanted to increase the size of data and also be able to handle files >4Gb so I changed Data to ext3 then I wanted to nuke WinXP (useless since Data in ext3), make it ext3, move root there, and merge root with Data to get a bigger Data partition.  I'll try the various suggestions thanks!

---

### Post by go_beep_yourself on 2008-12-01
> **sarc said:**
> Thanks for answers.  Yes I have several partitions: WinXP, Root, Swap, and Data.  I wanted to increase the size of data and also be able to handle files >4Gb so I changed Data to ext3 then I wanted to nuke WinXP (useless since Data in ext3), make it ext3, move root there, and merge root with Data to get a bigger Data partition.  I'll try the various suggestions thanks!

If you format a partition to ext3 or any filesystem, you will lose all files on it. Back them up somewhere first if you plan to do that. Winrar and p7zip allow you to split files. Theres also the split command in Linux and then you can put the files back together with the cat command.

---

