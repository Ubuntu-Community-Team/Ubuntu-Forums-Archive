---
title: "Grub repair no CD nor USB"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by mjbm on 2013-01-16
1. I have installed Xubuntu 11.10 on an old tablet Fujitsu Stylistic LT C-500 by pulling the HDD out of the tablet and put it in a desktop using an adapter as it has can’t boot from USB or CD.
2. The HDD has two partitions, all my data is stored in the logical partition.
3. It was working nice and fast until upgrading to 12.04 when it crashed getting the message “no such partition”.
4. Searched a little I have found I must reinstall Grub2.
5. When trying to use the method described in 1 again the HDD isn’t recognized.
6. I have placed it in an usb case attached to the desktop and booted from the cd rom with version 11.10; I can see the HDD, not the logical partition in it.
7. How can I repair the sistem whithout loosing my data?
8. I don’ know very much about commands, but I can copy :)

Mario

---

### Post by bodhi linux on 2013-01-16
Download linux puppy slacko 5.3.3 iso image,burn on cd or dvd,put in dvd drive when tourn on comp.(boot from cd).You will see partition of your hd.Put the usb stick.Copy data from hd to stick.Whit GPaarted format the hd,make more partition if you need.Install xubuntu again.

---

### Post by grahammechanical on 2013-01-16
Please explain this a little more.

>  I can see the HDD, not the logical partition in it.

What utility are you using? Is it file manager or Gparted - partition manager? Or Disks utility?

Another thing you might try, is when this HDD is in the Tablet call up the Grub menu by pressing Esc and select the Recovery mode option. That will give you an option to Update Grub Boot Loader.

[https://help.ubuntu.com/community/Grub2/Troubleshooting]("https://help.ubuntu.com/community/Grub2/Troubleshooting")

If re-installing make sure that to give that logical partition with your data on the mount point of /home but do **NOT** mark it for format. Your data will then be safe.

Regards.

---

### Post by mjbm on 2013-01-17
bodhi linux: Tried puppy booting from cd I can see the HD in the usb case but not the partition where my data is stored.

grahammechanical: I am booting from 11.10 Cdrom and using file manager to see the HDD in the usb case, not the partition I have mentioned before.

If I boot from USB I get a screen "GNU GRUB Version 1.99-ubuntu3.1"
but to any  command I get "error: no such partition"; I can get the terminal by pressing c, but to all commands I get the "no such partition" message.

Tanks,

---

### Post by Javelin Dan on 2013-01-17
mjbm - 

View my thread here: [http://ubuntuforums.org/showthread.php?t=2105897](http://ubuntuforums.org/showthread.php?t=2105897). I don't know if there's any help here or not, but you could try.

---

### Post by oldfred on 2013-01-17
Have you tried testdisk? You may be able to see old data partition, but it proably will not fix the issue of failed upgrade. Failed upgrade may be a lot more than just a grub reinstall, so I would try to backup data first.

       repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

    
       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

