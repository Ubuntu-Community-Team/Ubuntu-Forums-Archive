---
title: "Partition.."
date: 2011-09-24
forum: New to Ubuntu
---

### Post by ShawnxBuntu on 2011-09-24
Hi, yes Im very new to the Xubutu Seen.. I was just wondering if i could use GParted to Put more Space on Xubutu.. But theres one problem.. There alrdy 5 Partitions.. an it says ive alrdy maxed out my partitions.. to create a expandable partition or something.. But anyways.. I downloaded Xubuntu from the website but i did the dual boot... so i didnt have to create a partition.. how would i go about doing this?.. Or if Possiable could someone just tell me how to Uninstall Windows 7.. Maybe i could swap the Partition? to Linux or something? Idk like i said im very new...

  Partitions::
/dev/sda1  (File system) NTFS  Label Bios_RVY<--- I know thats not it.. diag 

/dev/sda2 (File System) NTFS  System  <---- but then where it says Flags says Boot,diag

/dev/sda3 (File System) NTFS /host/ OS Install <-- Thats where its at (Thats where Windows 7 is Installed at BUT THEN U SEE IM CONFUSED LOOK

/dev/sda4 (File System) NTS /data/ <--- That Stores all the data pretty Much im guessing.. thats how it was on windows 7.. OS_INSTALL C:, DATA D: <-- not sure about label but w.e

unllocated (File System) Unllocated <--- Shows  Size 1.02 MB...

 can someone help me?.. should i swap the data to linux.. Maybe the windows os will still be there cause if i go to C:\ which thats /host/ OS_INSTALL thats where /system32 is..

---

### Post by anewguy on 2011-09-24
I don't know if it's what you're running in to or not, because honestly it's been a while since I had to worry about it.

I think you created your partitions as primary partitions, and there is a limit to those, I believe 4.  What you probably need to do is start over on the partitioning and create an extended partition.  Within that partition you can create multiple logical partitions, even assigning drive letters (in Windows) to them.  However, with your current setup I'm not sure how you are going to do it, as I'm not familiar with the partitions you have.

Also - most PC's today have a recovery partition, and some even have 2 "extra" partitions - 1 for recovery and the other for something else dealing with recovery - in your case it looks to be some sort of boot to run diagnostics partition.  So that really probably only leaves 1 "regular" Windows partition plus whatever that data partition is.  But.....that is already 4 partitions.

Dave ;)

---

### Post by bodhi.zazen on 2011-09-24
You can only have 4 primary partitions.

You can add an extended partition and then have what are called logical partitions.

See: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

With gparted you can resize partitions, but you will need to back up your data first.

---

### Post by ShawnxBuntu on 2011-09-24
thats the thing i didnt partition xubuntu... so those partitions were already there...

---

### Post by bodhi.zazen on 2011-09-24
> **ShawnxBuntu said:**
> thats the thing i didnt partition xubuntu... so those partitions were already there...

You have to make space for Xubuntu, which means you need to completely delete at least one partition and then make room for Xubuntu.

Obviously you will loose any data in the partition you remove.

---

### Post by BEEDO on 2011-09-24
I haven't tried them but they're free:

[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

[http://www.minitool-partitionrecovery.com/recoverymore.html](http://www.minitool-partitionrecovery.com/recoverymore.html)

I had partitioning troubles/fears and am going the Virtualbox route for now.
Good Luck!

---

