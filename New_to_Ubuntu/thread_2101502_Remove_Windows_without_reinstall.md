---
title: "Remove Windows without reinstall"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by rmissildine on 2013-01-04
I too tried 12.10, and got the error about the  processor "PAE" not present, or something similar. I backed up to 12.04.01.LTS using the windows installer and got a good install. Since I too am new to Linux OS, a friend showed me his install, and I thought I'd give it a try on a spare netbook I have. My question is:  Since I'm currently using Ubuntu in dual boot mode, is there an app that will allow me to remove the windows os and keep the Ubuntu, or will I have to do a "clean" install using a cd or thumb drive? I like what I've seen so far, but want to get accustomed to the differences before I install it on the computer I use daily.

Thanks for all your help,
Roger

---

### Post by papibe on 2013-01-04
Post moved to its own thread.

---

### Post by Gone fishing on 2013-01-04
No need to do a reinstall, use the live cd to remove the Windows ntfs partition using gpartedthe partion editor then add a new ext4 partition. Reboot the system and in a terminal run sudo update-grub and Windows will be gone. You can then use the ext4 partition for storage etc

---

### Post by rmissildine on 2013-01-05
> **Gone fishing said:**
> No need to do a reinstall, use the live cd to remove the Windows ntfs partition using gpartedthe partion editor then add a new ext4 partition. Reboot the system and in a terminal run sudo update-grub and Windows will be gone. You can then use the ext4 partition for storage etc
Thanks for your reply Gone Fishing. Unfortunately, not being a software savvy person (my forte is in hardware), I'm not quite sure how to go about accomplishing the steps you outlined. Can you point me in the direction of a more direct approach, say, downloading an ISO file and making an install CD that will accomplish the desire result, that of reformatting the hard drive and having Ubuntu as the only OS? 

Thanks for all your help,
Roger

---

### Post by mlentink on 2013-01-05
this might help: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Mark Phelps on 2013-01-05
If you reformat the drive, the one that Ubuntu is on, you will erase the entire contents of Ubuntu -- not what you want to do.

The more direct approach would be to use an app known as GParted (Gnome Partition Editor) to remove the Windows partition and create a Linux partition in its place.

If you don't find Gparted using the Dash, you can easily install it using the Software Center.

---

### Post by arpanaut on 2013-01-05
In your original post you mentioned the windows installer.
Did you actually repartition your drive and do a full install.

Or do you have a wubi install.
With Ubuntu booted open a terminal and post the results of this command
```
sudo fdisk -lu
```

Just to make sure that we understand how your disks are partitioned.
If it is a wubi (windows installer) then if you delete windows you will lose both windows and Ubuntu.

---

### Post by Gone fishing on 2013-01-05
I assumed that this is normal install rather than a wubi install - as a wubi install takes place within the Windows file system you would need to do a full install before removing Windows.

Is this dual booting with it's own partitions - in which case my first reply is Ok or is it a wubi installed Ubuntu?

---

