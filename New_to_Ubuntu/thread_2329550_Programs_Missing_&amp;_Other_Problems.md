---
title: "Programs Missing &amp; Other Problems"
date: 2016-07-02
forum: New to Ubuntu
---

### Post by mukkun on 2016-07-02
Hi hi! I installed Ubuntu for an easy wipe of a system a few months ago since receiving a laptop from a friend and at the time it worked. Now it's been having a few problems- the Boot keeps filling up, certain key programs seem to have gone missing (such as certain system settings like Brightness), and yesterday I attempted to restart and it went a little crazy. I managed to sort things out enough to get the computer to let me back in but I'm worried about what may happen next time. I'm an absolute programming newbie so any help would be appreciated. The computer is a Toshiba Satellite laptop if that helps at all. Thank you!

Boot-Info @ [http://paste.ubuntu.com/18344534/](http://paste.ubuntu.com/18344534/)

---

### Post by oldfred on 2016-07-03
Did you really want & need full drive encryption?
That requires the advanced LVM logical volume partitioning plan which cannot use standard partition tools but requires the special LVM tools. 
Also with encryption, corruption can be difficult or impossible to fix since all data is encrypted. So a very good backup plan is required.

Because of above not recommended for newbies, unless you have to have encryption and then you have jumped into the deep end of the pool and must either sink or swim.

I do not know LVM, but have seen several installs with Boot-Repairs Summary report.

Since still 14.04 one of the required maintenance, is the removal of old kernels as you have a smallish separate /boot partition that can fill up. And that looks like one of your issues.
> /dev/sda1      ext2      236M  229M     0 100% /boot

Issue has been fixed in 16.04 where only two kernels are kept. There are many, many threads on the issue of full /boot partitions in forum.
You often get blockage of dpkg, and then have to manually delete a file or two in /boot, which then may also corrupt dpkg and require additional fixes. You normally never should manually delete a file that was installed and in dpkg list of installed files. 

Some of the standard ways to houseclean kernels are what you should be doing with every kernel update.
 /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove
# one line purge
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by mukkun on 2016-07-03
Thank you so much! You've been a big help and things are fixed now. Have a good day!!

---

