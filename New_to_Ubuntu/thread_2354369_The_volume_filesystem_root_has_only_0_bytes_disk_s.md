---
title: "The volume filesystem root has only 0 bytes disk space remaining"
date: 2017-03-02
forum: New to Ubuntu
---

### Post by doublemetre on 2017-03-02
Hello,

I'm a Ubuntu beginner and I installed Ubuntu and Windows 10 side by side a couple of months ago on my laptop but recently I got the following message "the volume filesystem root has only 0 bytes disk space remaining". Which is of course not good but I cannot access anymore on my Windows files from Ubuntu, it cannot be mounted because there is "no space left on device". With the *df* command I get the following :
```
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1962528        4   1962524   1% /dev
tmpfs             394732     1032    393700   1% /run
/dev/sda6       10442016  9929604         0 100% /
none                   4        0         4   0% /sys/fs/cgroup
none                5120        0      5120   0% /run/lock
none             1973644    31376   1942268   2% /run/shm
none              102400       44    102356   1% /run/user
/dev/sda5       30869380 24401920   4876324  84% /home
overflow            1024       56       968   6% /tmp
/dev/sda1         262144    76360    185784  30% /boot/efi
/dev/sda3       78096080 70898208   7197872  91% /media/mathias/OS

```
There is no space left on "/" so I guess I should clean it or give it more space but I have no idea how to do that and I don't want to start deleting random files and mess the whole system up :)

If you know how I could do that without breaking everything I would really appreciate!

Thanks a lot,

Mathias

---

### Post by Impavidus on 2017-03-02
Your root partition is only 10GB, which is rather small. It can work, but you can't install a lot of stuff and have to clean regularly. Your /home partition is almost full too. It's at 84% after a couple of months use, you won't need a lot of time to fill that completely.

Maybe you can clean things up to get a bit of breathing room. Clean old packages and autoremove old packages:```
sudo apt clean
sudo apt autoremove --purge
```Apt needs some room to work, but I think it may work, as there's still 500MB emergency room on that partition.

Which version of Ubuntu have you installed?

But it would be best if you made the Ubuntu partitions a bit larger. Use Windows to shrink the Windows partitions (if needed) to make sure you have unallocated disk space adjacent to the Linux partitions, reboot Windows a few times to let it run all its disk checks, then boot an Ubuntu live disk (the one you used to install Ubuntu) and make the Ubuntu partitions larger. Make sure you have backups of your important files.

---

### Post by doublemetre on 2017-03-02
Hi,

Thank you for your answer, 
I have already done clean and autoremove actually, my version is Ubuntu 14.04.5 LTS.
So you think the best way is to increase the size of the root partition? There is no other way to remove some things on this partition? 
For example if I re-install Ubuntu on it would it solve the problem?

Thanks again!

---

### Post by Impavidus on 2017-03-02
About 20GB is usually recommended for a root partition. You can remove some stuff, but not much, by uninstalling software, but I guess you installed your software for a reason. If you keep Ubuntu in a 10GB partition, it will be only a matter of time (a few months I think) before you get the same problem again.

---

