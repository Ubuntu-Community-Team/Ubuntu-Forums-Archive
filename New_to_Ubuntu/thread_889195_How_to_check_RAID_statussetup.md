---
title: "How to check RAID status/setup"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-08-13
I started off installing Ubuntu Server — everything seemed to go fine. On two 500 GB disks, I made a 10GB / partition, a 4GB swap partition, and a 486GB /home partition on each. Then I used the RAID 1 configuration menus to match all three partitions in pairs. Sprinkled throughout this were several choices (e.g., bootable flag on the / partitions). 

For other newbie reasons, I went through the install process a second time (long story, not exactly germane or interesting). When I got to the partition menu, the six partitions and the three RAID MDs were visible, but I couldn’t continue without going back and resetting certain things. I went in a few circles trying to figure it out, and eventually things looked right and I received no error message – the install went smoothly after that. 

Right after rebooting, I used “sudo apt-get install ubuntu-desktop” for GUI access, and everything *looks* ok. But my saying that is somewhat nonsensical – I don’t know what to look for. I can see that under properties of root and /home, I see the correct amount of free space. I’m not sure how to check the swap partition, and I have no idea how to check the status, setup, or integrity of the RAID array in either the GUI or the terminal. Webmin displays the correct device name, RAID level, and member disk devices, but I don’t know if there’s more to check.

Since I’ll be using this as a file server, knowing how is critical. Is such checking easily done in the GUI? Is there a relatively short batch of terminal commands? Is there a “care and feeding of your RAID array” How-To, book, or resource I can turn to?

Thanks, 

Rhythm

ETA:
Wow, RTFM, no? I'm spending a bit more time with Webmin and its documentation page, and I didn't realize there is more information within each module than what is first displayed. Between LINUX RAID and Partitions on Local Disks, it looks like I have enough feedback to have a sense of setup/status. 'Course, feel free to correct me if I'm wrong, and again, any reference to a book/resource/document with more information will be appreciated.

---

### Post by psusi on 2008-08-15
The command line tool for managing md software raid arrays is mdadm.  Check the man page for full documentation, but to just check the status of the array you run mdadm -D /dev/md0 to check the status of array 0.

IIRC, by default mdadm will send root an email when it detects a disk failure.

---

### Post by Ocelaris on 2008-09-17
This is the best guide I have found when setting up my linux file server

[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

more, not as straight forward

[http://linux-raid.osdl.org/index.php/RAID_setup](http://linux-raid.osdl.org/index.php/RAID_setup)

---

