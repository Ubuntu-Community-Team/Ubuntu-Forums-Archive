---
title: "Any pitfalls upgrading 12.04 to 14.04 with multiple partitions please?"
date: 2016-02-22
forum: New to Ubuntu
---

### Post by andrew-q2 on 2016-02-22
hello,   I’d to ask about upgrading please.
I’ve been running Ubuntu 12.04 LTS on a Dell laptop for a while now and would like to upgrade to the current 14.x LTS.
There are other partitions present - a Windows XP (installed first); and an Ubuntu Studio system; and a data partition.  I don’t want to mess up any of these when I upgrade.
So my question is please - are there any known pitfalls relating to upgrading?  I assume I should just go into Update Manager and click “upgrade” for 14.04.4.
Out of interest, will the upgrade tidy up the loader at boot time (Grub?).  This seems to have some spurious / duplicated entries, but it works fine once you know which to use.
thanks.  Andrew

---

### Post by oldfred on 2016-02-22
Best to houseclean before upgrading.
And make sure you comment out or uninstall any ppa or proprietary drivers.

I prefer clean installs as that also does houseclean, and restore /home and/or data. You also want to export a list of installed applications to make it easy to reinstall.
A few have had major issues with upgrade in place, and had to reinstall anyway, so make backups.

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

If grub menu has too many entries, you probably have not housecleaned kernels.
      
 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic

---

### Post by goofprog on 2016-02-22
Honestly, I don't know.  I would just back up the drive and give it a test or better yet copy the drive to another drive.

---

### Post by Mopar1973Man on 2016-02-22
I've typically got my root and home on different partitions. That allows me to just install from DVD to upgrade to the next version. The data on your home partition will be safe as long as you tell the installer you want to do something else. Then you can tell it the root partition and to format then the home partition to not format. As for other partitions like Windows etc should be safe as long as you don't reference them at all during the install. 

Above and beyond everything make sure you backup all data before you start! Like Murphy's Laws still applies... :-&

---

### Post by andrew-q2 on 2016-02-23
Thanks folks for the advice.  I'll have a look at the links etc.  It'll be a bit of a learning curve, for example I had no idea there were old kernels, I'm quite a novice on Ubuntu. Regards.

---

### Post by andrew-q2 on 2016-03-04
Just to say, I've upgraded, it seems to have worked very well, well done Ubuntu & people.  Retained my Home files.  Doesn't seem to have done anything bad to the Ubuntu Studio partition. Even kept my custom screen profile active. And the grub boot list is tidied up.  (I looked at tidying up before upgrading, but I wasn't getting anywhere fast, so just upgraded)   Cheers.

---

