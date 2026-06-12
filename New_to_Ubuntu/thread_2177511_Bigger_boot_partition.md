---
title: "Bigger boot partition?"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by Chris_Torok on 2013-09-29
Alright so my problem is as follows: I run Ubuntu 13.04, and I have a 1.5 TB hard drive. However, every 6 months or so, after an Ubuntu base update or a release update, I get an error saying that there is not enough room on my boot partition for the update to complete. To remedy this I've been removing the old, unused kernel versions from the partition using 'uname -a' and 'sudo apt-get -y purge (name of old kernel)'. Now I'm wanting to do one of two things: the first option would be to simply extend the boot partition to about 1 GB, it's at 273 and some odd MB right now (I've got a 1.5 TB drive, so I'm not really worried about the space). But I feel that this is only prolonging the inevitable, as those old kernels will eventually get backed up and fill the partition again. The only other option I can think of is to write a script into the updater that will delete the second to last kernel (so that the system would have fall-back kernel, should the extra current one fail) on the boot partition. However, I quite honestly have no idea how to attempt this. And as far as extending the boot partition goes, I have an idea of how to do it, but I'm not completely sure that I can do this and not over-write into another partition and seriously screw up my system. Any ideas?

---

### Post by TheFu on 2013-09-29
[http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) shows about the same thing you describe. It creates the command to run to remove old kernels and it wouldn't take much to have it DO IT.

---

### Post by oldfred on 2013-09-29
Generally desktops do not need separate /boot partitions, then the space of / (root) and all system partitions is shared in one. And then you can have /home or /mnt/data as partitions for data that take up most of the space. I have a 25GB / and only use about 9 GB of that including /home. But have all data in two data partitions.

I prefer to use synaptic to houseclean kernels. Several older threads have scripts, some one liners which I barely understand and others I pretty much do understand, but find synaptic more than adequate.

 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels 
dpkg --list | grep linux-image

      
 In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

     

If older from upgrade and not in synaptic
 cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic



       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by TheFu on 2013-09-29
I agree with almost everything Oldfred wrote. Synaptic is easier for beginners. Only provided the script link because the OP asked for a script - plus the script actually doesn't DO anything. It carefully generates a command with the list of kernels to be purged, leaving the current one out. I use this script and wrote it after a server, with a separate /boot, filled up and failed to install a new kernel. I find having a script easier then all that point-n-click myself.  To each their own.

I don't remember exactly when this became an issue - 10.04 didn't have the too-many-kernels issue.  I thought 13.04 was supposed to fix it by removing older kernels - but since I only use LTS, don't know from experience.

A separate /boot usually happens when LVM is used or when much of the OS is encrypted, IME. Good times.  I don't quite remember, but isn't LVM the default?  Perhaps that is only for the server installs?

---

### Post by Chris_Torok on 2013-10-04
Ah, that explains it. I installed this as LVM. I had originally planned to use this machine as a cloud server and my home PC, but I eventually bit the bullet and bought a pogoplug. So other than re-installing without LVM, there really isn't a permanent solution to this, is there?

---

### Post by sandyd on 2013-10-04
> **Chris_Torok said:**
> Ah, that explains it. I installed this as LVM. I had originally planned to use this machine as a cloud server and my home PC, but I eventually bit the bullet and bought a pogoplug. So other than re-installing without LVM, there really isn't a permanent solution to this, is there?

Wait - LVM you say?

LVM supports offline resizing (can do online expanding)., and will have to be done on a livecd

You will need to shrink the filesystem in the volume itself, and then shrink the LVM volume that contains the filesystem.

You can then expand the volume that contains the boot filesystem, and expand the boot filesystem after that.

---

### Post by TheFu on 2013-10-04
> **Chris_Torok said:**
> Ah, that explains it. I installed this as LVM. I had originally planned to use this machine as a cloud server and my home PC, but I eventually bit the bullet and bought a pogoplug. So other than re-installing without LVM, there really isn't a permanent solution to this, is there?

The permanent solution is to clean up old kernels from time to time.  Nobody has unlimited disk space.
However, if you do have extra storage, LVM will let you add that to the /boot partition. LVM is all about flexibility.
On a KVM server, the boot was automatically created to be 228MB - not big enough to avoid the same issue you have seen.  Resizing that to be 1-2G would make a huge difference, I suspect.

Plus don't forget that if you load kernel header files (some dependencies demand that), then storage on the other file systems will be used too.  **apt-get autoremove**

Just ran my script - it found 3 kernels to be cleaned up - running the autoremove found 10 header file packages to be cleaned up too.  The script isn't perfect for my needs ... time for some tweaking.  I can't wait for a post-inst script to be added to kernel installs that removes any more than 3 kernels on a system or a pre-install that checks for out-of-storage conditions and removes the oldest kernel before continuing.

---

