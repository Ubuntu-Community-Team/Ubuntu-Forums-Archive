---
title: "No space to install updates/Partitioning"
date: 2016-06-05
forum: New to Ubuntu
---

### Post by moon4 on 2016-06-05
Hi

To start from the beginning, when support for Win XP finished I install Ubuntu 14.04 on my desktop (an old custom built m/c that a friend gave me).  It worked fine for a long time and then suddenly I couldn't get Ubuntu to boot, so I reinstalled 14.04.  Now I'm finding it hasn't got space to do the updates.  I removed all my files and cleaned the system with Tweek and Bleachbit and it was fine for a while but I'm back at the 'no space' situation.

I tried to learn about partitioning but don't feel confident enough to try anything.  I did wonder if I've got some things twice having done two installations.  Is there a way to wipe the hd clean and start again?

These are my settings and disk info (using disks and gparted cos they show different things):
[ATTACH=CONFIG]269446[/ATTACH][ATTACH=CONFIG]269445[/ATTACH][ATTACH=CONFIG]269447[/ATTACH]

Is there anything wrong?  Is the hard drive just too small?

All advice gratefully received but please keep it simple, I'm a real beginner and have no programming knowledge.

Thanks
Moon

---

### Post by X-RED_Tech on 2016-06-05
Nothing wrong from your side. However, by selecting LVM, it created a damn small /boot partition (243MiB) that's filling up quickly with new and old kernels. It should by now create something bigger because there are many users in the same situation.
Bleachbit can remove old kernel temporarily giving space to breath to the OS but sooner than later it'll fill up again.
It's probably better not to use LVM for your home computer.

---

### Post by oldfred on 2016-06-05
Is the issue with /boot and updates to kernels?
Many have had that issue as they do not houseclean out old kernels. Finally with 16.04, the updates of a new kernel will clean out older ones and keep one older one and new kernel.

You have the separate /boot and LVM partitioning. I consider LVM an advanced partitioning system that adds complexity, but may offer some advantages. If you want full drive encryption you have LVM. 

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[URL="http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html"]http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html

[/URL]
 /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels) 

I prefer to use synaptic to remove old kernels:
      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a 
    [       ]("http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html")
 sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521) 
    [URL="http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html"]
[/URL]

---

### Post by moon4 on 2016-06-05
Thank you. So do I just delete the LVM partition using gparted? If I do that I assume I have to create a swap partition (as that seems to be in LVM) - do I then make the /boot partition as big as I can?

---

### Post by moon4 on 2016-06-05
Thank you - will the size of my computer cope with a 16.04 upgrade? I did check what kernels were there (from info in your links) and I only have one, so looks like Bleachbit has done its job.

---

### Post by oldfred on 2016-06-05
You only use gparted on the underlying physical partitions. You have to use LVM tools if using LVM.

A /boot partition is just for booting and not required if using standard partitions that you can use gparted with.
Standard default Ubuntu install is / (root) and swap. The /boot then is just another folder in /.

If not wanting full drive encryption and a newer user, probably better to fully remove the LVM & /boot and start over. Be sure to back up all your data. If you changed a lot of settings they are in /home. If you installed lots of apps, you an export a list to make it easy to reinstall. These processes should be part of your normal backup anyway.

Since your drive is smaller, I might just have the default install of / & swap.

---

### Post by X-RED_Tech on 2016-06-05
> **moon4 said:**
> will the size of my computer cope with a 16.04 upgrade?

If it runs 14.04 I'm 98,6% sure it'll run 16.04 as good as or better.

---

### Post by moon4 on 2016-06-05
Ooh that sounds the easiest solution then - thank you :)

Thank you everybody for your help.

---

### Post by moon4 on 2016-06-07
Hi All

Just wanted to say another thankyou - successfully installed 16.04 and now I have space back - thanks again

[IMG]http://i11.photobucket.com/albums/a176/moonlustie/Hard%20disk.png~original[/IMG]

---

