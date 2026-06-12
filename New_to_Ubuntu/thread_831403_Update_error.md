---
title: "Update error"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by EK228 on 2008-06-16
So I goto to get my updates, and when I click download, this error pops up:

E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

What the deuce does that mean, and who do I report it to? lol:)

Also might be unrelated or not, but occasionall my pc wont boot into the GRUB, it cant find the HD, so I just go into BIOS and search for the HD, it finds it, and then I can boot.

Odd....

---

### Post by avtolle on 2008-06-16
The first error message suggests a partition on your HDD that is full. Check your HDD to see if there is full partition. 
One way, from the terminal```
df -h
```

---

### Post by EK228 on 2008-06-16
Yes, it would appear that is what it says, here is what the command displayed.:

erik@erik-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             4.7G  521M  3.9G  12% /
varrun                601M  104K  601M   1% /var/run
varlock               601M     0  601M   0% /var/lock
udev                  601M   76K  601M   1% /dev
devshm                601M   12K  601M   1% /dev/shm
lrm                   601M   38M  564M   7% /lib/modules/2.6.24-18-generic/volatile
/dev/sdb7             183M   60M  114M  35% /boot
/dev/sdb3             4.7G  262M  4.2G   6% /home
/dev/sdb6             3.7G  2.0G  1.6G  55% /usr
/dev/sdb5             471M  470M     0 100% /var
gvfs-fuse-daemon      4.7G  521M  3.9G  12% /home/erik/.gvfs
erik@erik-desktop:~$ 


Some background, I took a Linux class in college, and one project was to partition my hard drive in accordance to the class.  Perhaps I did it incorrectly?  I see that /var is full....

---

### Post by avtolle on 2008-06-16
You will need to enlarge the /var partition, which is very small. To do so will require a live CD, be it Ubuntu 8.04, Gparted, or another of your choice. As you likely learned, resizing a linux partition affects it "at the end", not at the beginning. So, if there is some unallocated space on the HDD "at the end" of /dev/sb5, I'd use this space into which to enlarge the partition. If there isn't, but there is other "open space" on the HDD, things will get a bit trickier. Should the latter be the case, I'd back up the /var partition onto external media, then delete the current /var partition, and then create a new one of larger size, copying the contents of the current partition thereto. You will likely need to edit your fstab file as well, so the new partition is identified correctly, as I feel certain it will be provided a new device number.

EDIT: Sorry, forgot to post this link: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) which, although directly addressing creation of a new separate /home, provides the technique to create new specialized partitions to be applied in general. HTH.

---

### Post by EK228 on 2008-06-16
Excellent.  And I can pop in the CD I made and used to install Ubuntu 8.04 lts, correct?  I did leave some free space for just such a case.  I will simply increase the size of the partition, now, how big should I make it? 5 gigs?

---

### Post by avtolle on 2008-06-16
When the live CD boots (this is from memory) hit Alt+F2, then in the window type gksudo gparted, which should get you into the partitioner. If the Live CD kicks an error that gparted isn't installed (back in the day, one had to install it) then, get back to a terminal and type sudo aptitude update && sudo aptitude install gparted then try again. Once you are in the partitioner, something to be aware of: for reasons I don't understand, the darn Live CD mounts partitions to the desktop, and as you know, you cannot work with mounted partitions. If, when scrolling down to the /var partition, the program complains that it (that partition) is mounted, unmount it (cannot recall where the command is located; if all else fails, minimize the window, right click the icon on the desktop for the partition and select "unmount", then get back to gparted) and do your thing from there. I'd suggest a 2 gig partition, which should be more than sufficient IMO. HTH.

---

