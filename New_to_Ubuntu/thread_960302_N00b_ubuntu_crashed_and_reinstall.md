---
title: "N00b ubuntu crashed and reinstall"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by absintheminded on 2008-10-27
Hi,
I am a former Windows user, installed Ubuntu 8.04 to dual boot with Xp.

I paritioned the C drive 50-50. Now, for inexplicable reasons, ubuntu has crashed while XP is fine (hmmm... shouldnt it be the other way around? ;-)) and I am considering doing a full, clean reinstall of Ubuntu with the LiveCD on the new partition.

Question: When I put in the LiveCD and click the option install, will Ubuntu create another third new partition? What is the best way to go about the reinstall?

Thanks.

---

### Post by absintheminded on 2008-10-27
I guess my question is - I have already partitioned my disc 50/50 with ubuntu/XP through the first install with the liveCD. Now if I decide to reinstall and use the partitioner _again_ on the LiveCD and choose: "guided - use entire disk", will it wipe the entire HD with my XP installation or just the partition for ubuntu I created the frist time?

Any help greatly appreciated!

---

### Post by LowSky on 2008-10-27
Choose manual partition
for linux use the partiton that is not, repeat not NTFS. label the one that isn't NTFS, "/" without quotes. The formate should be ext3.

Hope that helps

---

### Post by absintheminded on 2008-10-27
Thanks. When I get to the manual option installation I see three partitions in the window:

/dev/sda1/ NFTS (I guess its the one with Windows)
/dev/sda5/ ext3 (I guess old Ubuntu)
/dev/sda6/ swap

You mentioned I should rename the ext 3 parition? How do I do that? 

Also to continue overwriting my old install of ubunty, do I simply select the _ext3_ parition and click "Forward" button?

Sorry if this is really simple but I want to make sure I don't do anything wrong.

---

### Post by LowSky on 2008-10-27
Choose the ext3 patition click on edit under "mount point" just put ```
/
```

click ok and start instalation

---

### Post by absintheminded on 2008-10-27
Ok, I have clicked on edit partition, but no renaming option comes up.

Just the following

Use as: (choose between "do not use partition" and "fat32, ext3, etc"

Format the partition: (a box to tick)

Mount point: (choose between "/", "/boot" "/home" etc)

--

I assume I have click the box and move it from "do not use partition" to "ext3".

I'm not sure whether I should tick the "format the partition" box.

To rename I guess you set the mount point to "/"

And then press forward to go on with the reinstallation.

Correct?

Thanks.

---

### Post by LowSky on 2008-10-27
sorry moint point to /

my mistake i'm at work on a windows machine

yes make it ext3
and yes format partition

---

### Post by absintheminded on 2008-10-27
thanks! this issue has been solved.

---

