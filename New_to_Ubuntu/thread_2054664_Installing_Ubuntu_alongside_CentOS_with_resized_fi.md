---
title: "Installing Ubuntu alongside CentOS with resized filesystem?"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Frank O on 2012-09-07
Recently I installed CentOS 6.3 on a 64-bit laptop with a brand-new, completely blank 500GB hard drive. During the installation I told CentOS to use the entire hard disk.

I've now decided that I would like to have Ubuntu and CentOS installed alongside each other on this laptop. The staff of the CentOS forum suggested that I use **resize2fs** and **lvresize** to reduce the size of its filesystem and logical volume to 100GB (in CentOS, my filesystem is at /dev/mapper/vg_acer-lv_home ).

I've completed these steps, seemingly successfully. The CentOS folks indicate that it should now be possible to install another Linux OS "as it can also use LVM and share the space."

Can you give me any guidance on exactly how I should proceed with the Ubuntu 12.04 install CD to accomplish this?  I assume that, once installed, both Ubuntu and CentOS will appear on the grub splash screen during normal bootup from the hard disk -- is that the way dual Linux OS's are usually installed?

If I could get a better or cleaner install by wiping the hard drive and starting over, that wouldn't be too much of an issue, as I really haven't customized CentOS much or stored any data on the system.

---

### Post by critin on 2012-09-07
I know nothing about Centos, but ubuntu is easy to set up dual boots.  You might want to check this.  The version of ubuntu is different, but the instructions should be the same.

[http://www.youtube.com/watch?v=m0VW9w8F53I](http://www.youtube.com/watch?v=m0VW9w8F53I)

---

### Post by oldfred on 2012-09-07
With LVM, you have to use the alternative installer. The standard desktop install does not include server type drivers like LVM nor RAID drivers.

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Or you can just shrink the LVM and create another partition outside the LVM. The advantage of LVM is that you can resize partitions on the fly and move things around easily, but it adds a level of complexity. You cannot use gparted on LVM and have to use some other tools also.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

Often good to have a liveCD but then you have to add the lvm drivers each time you boot liveCD.

# ("apt-get install lvm2" in debian based distros)
sudo apt-get install lvm2

I know one user with Fedora said to install without its default of LVM as it does not add much, not sure about CentOS.

---

### Post by Frank O on 2012-09-07
> **critin said:**
> I know nothing about Centos, but ubuntu is easy  to set up dual boots.  You might want to check this.  The version of  ubuntu is different, but the instructions should be the same.

[http://www.youtube.com/watch?v=m0VW9w8F53I](http://www.youtube.com/watch?v=m0VW9w8F53I)

Thanks for the reply. I'd run across that video when I was doing web searches for information on dual Ubuntu/CentOS installs.  It seems to assume, however, that you have Ubuntu installed first and are adding CentOS, whereas my situation is the other way around.

> **oldfred said:**
> With LVM, you have to use the alternative installer. The standard desktop install does not include server type drivers like LVM nor RAID drivers.

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

Or you can just shrink the LVM and create another partition outside the LVM. The advantage of LVM is that you can resize partitions on the fly and move things around easily, but it adds a level of complexity. You cannot use gparted on LVM and have to use some other tools also.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

Often good to have a liveCD but then you have to add the lvm drivers each time you boot liveCD.

# ("apt-get install lvm2" in debian based distros)
sudo apt-get install lvm2

I know one user with Fedora said to install without its default of LVM as it does not add much, not sure about CentOS.

As a Linux newbie, I have to say that the links above are very helpful but taking me to a level of complexity I'm probably not ready for.  At this point I don't have any strong feelings about whether to use LVM or not.  My objective is really just to get Ubuntu installed alongside CentOS; I doubt I would be taking advantage of the flexibility that LVM provides to resize partitions for quite some time to come (if ever).

So maybe I should rephrase my question.  What is the *easiest* way to get Ubuntu installed alongside my existing install of CentOS with its resized filesystem and logical volume?

---

### Post by Epodx64 on 2012-09-07
Here's something I do for dual boots if you have an extra Harddrive laying around I use to have Scientific Linux installed on one HDD and Kubuntu on another and I'd just select which HDD to boot first from the bios works perfect.

---

### Post by oldfred on 2012-09-07
Several have posted with Fedora in a LVM partition but not really using the LVM, as it still is just one partition (logical matches physical). Then the other partitions are used as normal primary, or logical partitions. You can then install Ubuntu into a logical partition, but it will depend on what partitions are now used.

---

