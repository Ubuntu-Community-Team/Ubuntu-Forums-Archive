---
title: "Install options - which one ?"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by michael-piziak on 2014-03-15
My sister ordered an Ubuntu disk (12.04) and we are trying to install it on half of her system and leave the other half with Windows Vista.

We've come upon the attached screen and we don't know what to choose.   Please help.

I don't know why her install disk acts like this, my install disk asked easy questions when I installed.

---

### Post by buzzingrobot on 2014-03-15
That's the screen that is displayed when you select the "Something Else" option on the screen that includes the option to install Ubuntu "alongside" Windows (or whatever OS is already installed).

What you see listed there are the partitions created and used by Windows. If you delete them, you will delete Windows.

A "Back" button ought to be visible in the lower right corner. Clicking it should take you back to the screen where you can choose to install Ubuntu alongside Windows.

Rather than simply backing up, I would suggest rebooting and starting over.

*If* you do not see the screen offering the choice to install alongside Windows, or there is no "Back" button in the above screen, the Ubuntu installer is not working correctly, most likely due to an error in the disk.  

But, that, however, seems very unlikely to me.  Just proceed steadily through the process. It can take a bit of  time to move between sections, so if you know you have clicked on something, don't get impatient and click it again.

Ubuntu 12.04 (and Ubuntu 12.04.04 -- a version with an upgrade Linux kernel and graphics software) can be downloaded here:  [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by michael-piziak on 2014-03-15
On her disk, it only gives 2 options

1) Erase disk and install Ubuntu  (warning this will delete everything)

2) Something else - you can create or resize, partition, or choose multiple partitions for Ubuntu

When she selects #2 it brings up the same screen that I attached.

We are puzzled what to do.

---

### Post by buzzingrobot on 2014-03-15
If Windows is occupying the entire disk, there will be no available space in which to install Ubuntu. In that case, it would be pointless to offer an option to install alongside Windows, and a jump to the screen shown to you would make sense.

If Windows is occupying the entire disk, then you need to reduce the amount of disk space it occupies to create room for Ubuntu, by shrinking the partitions it uses.  Here is the page on the Ubuntu wiki that discusses shrinking the size of Windows partitions:  [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions).  Proceed with care and backup any files you do not want to risk losing.

Perhaps someone else can offer something here.

---

### Post by 3rdalbum on 2014-03-15
I can't see the screenshot on my phone, but it sounds to me like that computer already has four primary partitions, which is the maximum you can have.

If it had 3 or less you would have the option to resize Windows.

You will need to use that screen to remove one partition that you don't need, and then create a partition for Ubuntu with the type "ext4" and the mount point "/".

---

### Post by JKyleOKC on 2014-03-15
> **3rdalbum said:**
> I can't see the screenshot on my phone, but it sounds to me like that computer already has four primary partitions, which is the maximum you can have.

If it had 3 or less you would have the option to resize Windows.

You will need to use that screen to remove one partition that you don't need, and then create a partition for Ubuntu with the type "ext4" and the mount point "/".The screenshot shows only two partitions, identified as sda1 and sda3 and both are NTFS. They total about 750 GB, which is not a usual size for a hard drive. This is **NOT** a typical result, so I suspect a defective CD/DVD. There should be a line in the first menu displayed at boot time, to "check the CD" or words to that effect. I would do so.

If the disk is defective, try burning a replacement, at the lowest possible speed. High-speed burns seem to often introduce errors...

---

### Post by Impavidus on 2014-03-15
Just two partitions, so the installer should offer to install Ubuntu alongside Windows. That fact that it doesn't could indicate a faulty installer disk, but it could also be a damaged ntfs file system. I think the installer refuses to resize damaged ntfs systems. But it's best to resize Win Vista partitions with Windows tools anyway.

Try this: boot Windows, let it do any file system checks it wants, resize the Windows partitions to make some room for Ubuntu and reboot a couple of times to let Windows run it's file system repairs. Then try again installing Ubuntu. It may give you the option to install Ubuntu alongside Windows.

---

### Post by evan8 on 2014-03-15
Maybe it's different since he is using Vista and not windows 7? Not sure.

---

### Post by QIII on 2014-03-15
That's a Seagate Barracuda 7200.11 750GB drive.  Not uncommon about 2008/2009.  But I would be sure that the firmware on that drive has been updated so that you don't run in to the "busy loop" error some of those drives were notorious for.

I would suggest 2x defrag and then shrink/modify the partition sizes *with the Windows utility.*

Then the "along side" option should show up.

---

