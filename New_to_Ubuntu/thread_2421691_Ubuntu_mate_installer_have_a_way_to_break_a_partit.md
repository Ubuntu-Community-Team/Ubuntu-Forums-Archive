---
title: "Ubuntu mate installer have a way to break a partiton in two"
date: 2019-06-25
forum: New to Ubuntu
---

### Post by kromak on 2019-06-25
Hello. I wish to install Ubuntu mate on a partition that already has data on it. To make the data independent on the OS, so I can reinstall Ubuntu Mate on the future without loss of data, I wish to divide that partition on two, keeping about 7.5GB for Mate, and the rest for the data. But looking at the installer now (I am currently running it) it does not seem to possess the capability of splitting one in two. Is that right, I cannot do so through the installer? Will I have to look for another program to do so ? If yes, can you recommend one?

Thanks for the help.

---

### Post by ajgreeny on 2019-06-25
I do not know the xfs filesystem at all but I assume you can use gparted which is probably on the live USB you're using to install Ubuntu-Mate to reduce the size of the partition you are asking about, though it is not possible to see how far you can shrink the partition, as we can not see how much of it is currently used by the data.

The default filesystem for Ubuntu OSs is ext4; is there a reason for your choice of xfs?
I am not saying it is a bad choice but I am simply interested in understanding the reason for your choice.

---

### Post by oldfred on 2019-06-25
Please do not post screenshots in line.
You can easily attach with Forum's advanced editor and the paperclip icon.

While bug is older & says fixed, posts seem to indicate some issues are still there.
        if / or /boot not ext4, then insmod may be required in /EFI/ubuntu/grub.cfg & .mod file copied. Bug on xfs
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822)

---

### Post by kromak on 2019-06-25
> **ajgreeny said:**
> I do not know the xfs filesystem at all but I assume you can use gparted which is probably on the live USB you're using to install Ubuntu-Mate to reduce the size of the partition you are asking about, though it is not possible to see how far you can shrink the partition, as we can not see how much of it is currently used by the data.

The default filesystem for Ubuntu OSs is ext4; is there a reason for your choice of xfs?
I am not saying it is a bad choice but I am simply interested in understanding the reason for your choice.

Hi, it is because Ext4 do not work with my Old Ubuntu 10.04. I launched gparted and will try to shrink and then split the old partition. By the way, I am not using live USB.


******EDITED*******

Thinking well,  > Ext4 do not work with my Old Ubuntu 10.04 does not make any sense, since it`s an old tech. In fact, I am sure I used it in the past. I was thinking in btrfs. The reason I chosen ti do not use Ext4 was probably because it wastes too much space with journaling or safety features.

---

### Post by kromak on 2019-06-25
> **oldfred said:**
> Please do not post screenshots in line.
You can easily attach with Forum's advanced editor and the paperclip icon.

While bug is older & says fixed, posts seem to indicate some issues are still there.
        if / or /boot not ext4, then insmod may be required in /EFI/ubuntu/grub.cfg & .mod file copied. Bug on xfs
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822)

Sorry. Will try to edit it. Don`t know how to use this paperclip icon. All I see is a little icon with a tree inside, left to the quote button.

And thanks for the warning. Fortunately my pc does not support EFI.


********EDITED*********
GParted is not allowing me to change the partition size. The partition I want to resize is dev/sda1 with has about 7GB of free space. If I select it with a mouse click and then go to the resize/move option on the "partition" menu option, it opens a dialog box where there is "Free space preceding", "New Size" and "free space following" and then "align to". All the three first fields cannot be changed. The other partition where Lucid Lynx is installed, also cannot be resized. Why is that happening? The partition is of kind MSDOS, the first partition is /dev/sda1 with a boot flag. The one with Lucid Lynx is /dev/sda5 with out any flag


*******EDITED2*******

There is place on gparted with the name "File System Support"
And there it is? Xfs does not support shrinking. With means I am doomed and will not be bale to install it, unless there is a way to convert a xfs to reiserfs  or ext4 that supports  it.

---

