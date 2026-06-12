---
title: "Using Gparted"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by Electronicman on 2012-07-13
I want to be able to have both Ubuntu 11 and 12 on the same disc. When I installed Ubuntu 11, I told it to use the whole disc, now I would like to install Ubuntu 12, and I need to re-partion the disc to make some room. How do I go about this?

Here is a screen shot of my second drive

---

### Post by Vaphell on 2012-07-13
you must boot some livecd/usb to run gparted because you can't work on mounted and utilized partitions. You should have an option to shrink partition there.
[http://gparted.sourceforge.net/larry/resize/big/operations-b.gif](http://gparted.sourceforge.net/larry/resize/big/operations-b.gif)
then you create new partition(s) using the freed space.

Consider creating additional partition that will store shared data - let's say 20GB ubuntu1, 20GB ubuntu2 and Data occupying the rest. You would mount that partition to gain access to the data. Advantage is that you can easily reinstall systems on those system partitions, should the need arise, or install something else over without putting personal data on the line and risking losing it.
Having smallish /home partitions to store only user settings would be nice too. Separate /homes remember your settings after reinstall if you don't reformat them during the install procedure.
Needless to say, to achieve such a setup you have to forget about installation wizards that do stuff automagically, and use gparted based manual mode.

---

### Post by Kopkins on 2012-07-13
Do what the previous poster said. They gave you the right idea. Shrink the large partition you have and make new partitions from the resulting free space. 

If you want to do what Vaphell said, making separate /home partitions for each, the easiest way would be to reinstall 11.xx, as your current partition scheme uses only one partition for /root and /home. 

As they said, you'll have to rely on manual partitioning for this, you can't let the system do it for you.

Best of luck,
Kopkins

---

### Post by Electronicman on 2012-07-14
Thanks for the advice, sounds like a good idea.

What happens to Grub in this case, now I have a dual boot WIN and Ubuntu. With two Ubuntu's  I will end up with a triple boot, will I therefore have an option and how would this look in the boot menu?

---

### Post by Sef on 2012-07-14
> What happens to Grub in this case, now I have a dual boot WIN and Ubuntu. With two Ubuntu's I will end up with a triple boot, will I therefore have an option and how would this look in the boot menu?

You would have an extra os to boot into, otherwise, all would look the same.

---

### Post by Kopkins on 2012-07-14
Like Sef said, you'll just have a few extra options. 

On the new install it will install grub and auto detect the systems already there.

Kopkins

---

### Post by Electronicman on 2012-07-16
I now am the proud owner of a triple boot computer. Everything appears to work correctly. I chickened out of having separate Home partitions, and let the system install Ubuntu 12 side by side with Ubuntu 11.

One question however, I am not able to see Ubuntu 11 from Ubuntu 12, and visa versa, but I can see Windows from either of them. Is there something I can change? or have I screwed up.

Here is a shot of the partitions

---

### Post by oldfred on 2012-07-16
Do you mean booting or the system partitions?

If booting 
sudo update-grub

but that only helps on the version in the MBR of your boot drive. That would be the one first on the grub menu.

If you want to see the partitions from Nautilus, it should be there. I prefer to label my partitions as I have many and have trouble keeping track. But I also suggest that you shrink the system partition(s) and make a data partition to share data if you are going to regularly boot both systems and want the same data in both. I used both NTFS shared data partition so I have the same bookmarks from Firefox in all my installs and LInux formated for all new data as I now do not boot XP.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

