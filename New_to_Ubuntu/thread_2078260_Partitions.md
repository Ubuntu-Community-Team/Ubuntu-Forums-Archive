---
title: "Partitions?"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-30
Hi,

Here is my new plan is it fine?

1. / 30 GB ext4 Primary.

2. /home 144 ext4 Primary.

3. swap 4 GB Primary.

4. Extended > Logical 120 GB NTFS created using GParted for creating & restoring back ups.

5. Should a mount point like /dos or /windows be given to the NTFS partition created by GParted, during Ubuntu install OR a file system name or left alone?

6. Will this NTFS partition help in storing & restoring created backups?

7. What should be backed up......./ or /home or both & which is the most dependable app for creating restoring Ubuntu back ups?

8. Should /, & /home be formatted during install?

The reason for asking multiple simple questions is that don't want to be reinstalling, resizing, creating partitions for Ubuntu as it's size grows, NTFS for creating/restoring it's back ups etc......hope you understand my situation. 

Thanks.

---

### Post by Cheesemill on 2012-10-30
If you're not going to be dual booting with Windows then don't use NTFS, you should stick with ext4.
When there is a problem with an NTFS partition often the only way to fix it is by running Windows.

Also if this is going to be used for backups I suggest having this partition on a separate drive. The main reason for needing a backup is if your drive fails, obviously if your backup is on the same drive as your data then it is of no use in this situation.

---

### Post by pkadeel on 2012-10-30
After a lot trials, I settled on partitioning my 500G drive as follows;

/boot = 200MB
swap = 4GB
Logical partition = 350GB
-> / = 30GB
-> /home = 50 GB
-> three more partitions  70GB for virtualbox (you might not need that), 100GB for multimedia/pictures etc & 100GB for other data archives
Rest of the disk is not partitioned. I keep backup of these  3 partitions on a separate USB drive.

As for /home I don't use it much for storing data. Only things to do currently and when finished, shifted to the 3rd archive partition.

For file system if you do not plan to use windows then NTFS is of no use and specially i don't think it would be a good idea to use NTFS on / and /home if you do intend to use windows. I think ext4 is the best option for ubuntu.

---

### Post by Mark Phelps on 2012-10-30
Just for clarification -- you can't use root (/) and /home filesystems on NTFS partitions.  Those are Windows partitions and will not be able to handle the Linux filesystem permissions needed to run Ubuntu.

Also, while I'm a big fan on using NTFS partitions to share data between Windows and Linux, for Linux backups, you would do better using Ext4, not NTFS.

---

