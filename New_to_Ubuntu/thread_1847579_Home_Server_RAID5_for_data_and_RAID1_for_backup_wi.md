---
title: "Home Server RAID5 for data and RAID1 for backup with Mythbuntu backend"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by mikodo on 2011-09-21
I am reading about using RAID for a  Mythbuntu Backend home server. I came across this thread: [http://ubuntuforums.org/showthread.php?t=1444597]("http://http//ubuntuforums.org/showthread.php?t=1444597")

In post #3 ian dobson made the following statement:

[B][I]"I have a large RAID5 array (4 * 2Tb wd drives). If one drive dies the  RAID array can handle it (add a now one and add to array). I also have  2*2Tb wd 4Kb drives in a RAID1 stripe for backups, if I delete a file by  mistake/the file system screws up.

This makes it alot easier to handle all my data rather than having it split over different drives".[/I][/B]

Questions:

1.) Would the RAID5 allow for one drive to fail, and still keep the data intact allowing the failed disk to be replaced, without loss of data to the array? (Assuming the writable data volume on the failed disk, is same as the writable data volume on the other disks; I think).

2.)  Would the RAID1 be a good backup of the data for the RAID5. If so, how does that work? Wouldn't any data loss/corruption on RAID5, be reflected on the RAID1 disks?

3.) Could both the RAID5 & RAID1 disks, be in the same server?

If this works as outlined; I am excited about it :^)

Thanks.

---

