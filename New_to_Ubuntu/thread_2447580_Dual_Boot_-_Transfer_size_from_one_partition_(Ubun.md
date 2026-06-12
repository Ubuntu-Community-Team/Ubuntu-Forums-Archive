---
title: "Dual Boot - Transfer size from one partition (Ubuntu) to the other (Windows)"
date: 2020-07-21
forum: New to Ubuntu
---

### Post by edualvarado on 2020-07-21
[COLOR=#242729][FONT=Arial]I have dual-boot. I am currently running out of space in my partition with Windows (/dev/**nvme0n1p3**). However, there is plenty of space in my partition with Ubuntu (/dev/**nvme0n1p6**). Therefore, I would like to move 70 Gb from Ubuntu to Windows.

[/FONT][/COLOR][COLOR=#242729][FONT=Arial][FONT=inherit]How can I do this, in order to transfer safely space to Windows? I already have Ubuntu in my USB, and I know that I should use GParted from it. But I do not know how to deal with GParted, moving to right/left the spaces and so on. I don't want to mesh it up. 

How should it be done, step by step?

Thanks![/FONT]
[/FONT][/COLOR]

[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/lFW8v.png[/IMG]

---

### Post by oldfred on 2020-07-21
Please attach screenshots. Easy to do with Forum's advanced editor and paperclip icon.
Or for partition info, just use fdisk or parted & copy & paste terminal output. Better in code tags or # icon in advanced editor.
sudo parted /dev/sda unit s print
sudo fdisk -lu

You put swap between Windows NTFS partition and Linux / (root) partition. 
So now it is more difficult. New versions of Ubuntu do not need swap partition as they use swap file, but if you create a swap partition then it is used.

You can with gparted delete swap, shrink Linux partition, create new swap just before p4, edit fstab with new UUID for swap or it will not boot, move / (root) right.  Best to do one step at a time. You must use live installer as you cannot change mounted partitions.
Then use Windows tools to expand NTFS partition.

Easier option may be just to shrink Linux partition and create a new NTFS data partition. You can then share some data between Windows & Linux, but have to have Windows fast start up off as that sets hibernation flag, so then Linux NTFS driver will only mount read only. Default mounts then fail. And Windows turns fast start up back on with updates.
If sharing data, better to have separate data partition as you really should only mount the Windows system partition as read only in all cases to prevent accidental damage. The Linux driver opens all normally protected files & folders.

---

### Post by ActionParsnip on 2020-07-21
If you have a swap partition and set one at install will this be used instead of a swap file, please? Just read the last reply and was curious

---

### Post by oldfred on 2020-07-21
I have an old swap on two drives, but have to click on them and say do not use.
Then installer creates a swap file.

Some still like a swap partition and if you have one it normally will be used, automatically.

---

### Post by edualvarado on 2020-07-22
Thank you for your answer, but I did not totally understand the process. In this sentence:

> You can with gparted delete swap, shrink Linux partition, create new swap just before p4, **edit fstab with new UUID for swap or it will not boot, move / (root) right.** Best to do one step at a time. You must use live installer as you cannot change mounted partitions.


What do you mean with the bold part?

Like, step for step, should be:

1. With bootable USB, go to GParted
2. Delete swap
3. Shrink Linux Partition **->** **Do I shrink from the right or from the left?**
4. Create new swap and move it to the right before p4.
5. edit fstab with new UUID for swap or it will not boot[B] -> Don't understand what you mean here.
[/B]6. move / (root) right[B] -> What do you mean with  /(root)? The partition where Ubuntu is installed? In this case, how much to the right? Totally at the end?
[/B]
If you could be a little bit more specific I would really appreciate it.

Here is another capture of the partition system, this time from Windows.

[IMG]https://i.imgur.com/cf9XZHM.png[/IMG]


Thank you.

---

### Post by oldfred on 2020-07-22
This will show UUIDs.
lsblk -f
This will show fstab as it is currently. The UUID for swap should be in list above.
cat /etc/fstab

But when you delete swap, the entry in fstab will not work as it does not exist, so you can comment it out first with # at beginning of the line. 
sudoedit /etc/fstab
Then when you delete swap using gparted from live system, installed system will still boot.
And then once you have created new swap with gparted. Reboot & see new UUID for new swap partition
lsblk -f
And edit fstab to replace UUID of old swap with UUID of new swap & remove #.
sudoedit /etc/fstab
Always check that any changes are valid by remounting, if no errors then ok, or you have to fix error before rebooting.
sudo mount -a

---

