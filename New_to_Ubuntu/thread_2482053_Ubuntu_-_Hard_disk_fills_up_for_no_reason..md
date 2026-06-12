---
title: "Ubuntu - Hard disk fills up for no reason."
date: 2022-12-17
forum: New to Ubuntu
---

### Post by arnold4529 on 2022-12-17
I have a problem with Ubuntu and I noticed that my hard disk indicates that it is almost completely full, but when I check the files, I should have plenty of storage space left over.


I ran the command df -h and this is the result of one of the partitions. 
Filesystem Size Used Avail Use% Mounted on 
/dev/nvme0n1p5 110G 104G 363M 100% /


But when I enter Disk Usage Analyzer, it tells me that I am only using 34.4 GB.


Note: This came up after I ran the sudo rm -r command to delete a folder. I have already checked the Trash and it is empty.

---

### Post by TheFu on 2022-12-17
Don't trust GUI tools.

There are a few threads in these forums that explain how to find which area and files are eating storage. Search and read those.  Rehashing the 10 commands isn't worth it here, IMHO.

BTW, if you are using btrfs or ZFS, you cannot trust what du or df say.  Use the volume manager's tools instead.

---

### Post by arnold4529 on 2022-12-17
> **TheFu said:**
> Don't trust GUI tools.

There are a few threads in these forums that explain how to find which area and files are eating storage. Search and read those.  Rehashing the 10 commands isn't worth it here, IMHO.

BTW, if you are using btrfs or ZFS, you cannot trust what du or df say.  Use the volume manager's tools instead.

[COLOR=#000000]I think it is not only in GUI where it tells me that I am using less space. Even when I enter the file explorer, I can see that my disk only has a few MB available. But when I go into the disk and select all the files it has (even the hidden ones) and hit properties, it tells me that the weight is much less than what it tells me I have already consumed.[/COLOR]


[COLOR=#000000]Could you tell me in which thread, I've been looking for a while and I can't find it.[/COLOR]

---

### Post by deadflowr on 2022-12-18
> Could you tell me in which thread, I've been looking for a while and I can't find it.
There are probably a dozen or so threads about this type of thing from the last year,
but this thread is an oldie but a goodie:
[https://ubuntuforums.org/showthread.php?t=1122670]("https://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by grahammechanical on 2022-12-18
This is my uneducated guess on this matter is:

The full printout from the df -h command would have showed a long list of loop devices. These are files (of a relatively small size) that are viewed by the df command and the GUI utilities as file systems of a much larger size. These loop devices are not actually taking up all that space on the drive. 

Regards

---

### Post by yancek on 2022-12-18
> /dev/nvme0n1p5 110G 104G 363M 100% / 

The above output shows that your root filesystem partition is full.  You may have a lot of unused space on other partitions but that is not relevant.

You could look for log files in the /var directory and delete them to create more space.

---

### Post by deadflowr on 2022-12-18
Thinking it through, Disk Usage Analyzer only shows outputs for what you can read as a normal user.
So most prominent of directories you cannot read as a normal user would be the /root directory.
So probably check that one out.

---

### Post by TheFu on 2022-12-18
> **arnold4529 said:**
> [COLOR=#000000]I think it is not only in GUI where it tells me that I am using less space. Even when I enter the file explorer, I can see that my disk only has a few MB available. But when I go into the disk and select all the files it has (even the hidden ones) and hit properties, it tells me that the weight is much less than what it tells me I have already consumed.[/COLOR]


[COLOR=#000000]Could you tell me in which thread, I've been looking for a while and I can't find it.[/COLOR]

"file explorer" is a GUI tool.  Don't trust it.  If you are not typing into a terminal, don't trust it. If you are using a mount to click anything, don't trust it.

Anyway, there are probably 10 threads to see how storage is used. The link above is good. There are others that have specific examples.  A possible issue is to have run-away log files. Logs that fill up the space.  There is a thread about that here too and steps to take to 
a) figure out the root cause (it is never "no reason")
b) limit the size for logs
c) rotate log files
For a normal desktop system, there is little reason to allow logs to get over 100MB total size, so that would be the limit I'd set.  If they do get over that size, it is almost always because of a repeating message that you are unlikely to miss.

Below isn't about fixing the specific out of storage issue. It is how to solve the problem, gain more security, and have a more stable system.

Don't know if you've heard this before, but long-time Linux/Unix users will setup /var/ onto a different partition to avoid filling the / partition.  Same for having a separate /home/ for home directories.  Unix-like OSes don't like full disks. It makes them slower and unstable.  There are other reasons, usually for security purposes since different mount options can be used for each partition, but not if they are all the same.  

Canonical has made the choice that the default storage setup should be simple, which is fine, until something bad happens.  Creating and moving data to different partitions and mounting those isn't exactly a beginner task, but it isn't THAT hard. Definitely not an advance task either.  If you are afraid of the shell/CLI, forgetaboutit.  If you need to be told exactly what to type, without understanding, forgetaboutit.  But if you can figure out what to do based on broad instructions, it is fairly easy with some basic skills like partitioning, mounting, rsync, and permissions management.  The goal is simple, move all the files under /var/ to a new partition in a new mount location, then mount that specific partition back to /var/ using the /etc/fstab for the original OS.  This is handled easiest using a "Try Ubuntu" or  "Live Boot" environment.

---

