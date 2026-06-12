---
title: "[SOLVED] External Disk Drives - The 'names' keep changing"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by canam101 on 2008-11-06
I have an external disk drive with 3 partitions, a, b, and c.

At the moment a is seen by the system as /media/disk-1, b as disk-2, and c as disk-3

If I reboot, there is a good chance, based on what has happened before, that the system will mix up the three 'names' it has, so that a may become /media/disk-2, b may be /media-disk-3, and c may be /media/disk-1.

This screws up several scripts I run nightly that do backups. Is there anything I can do to make the system keep the same names for each partition?

---

### Post by drs305 on 2008-11-06
Yes, you can put them in fstab, if they are not there already, and identify them by either UUIDs or labels.

If you need help with this, post the results of:
```

sudo blkid
cat /etc/fstab
mount

```

For specific advice, also tell us the desired mountpoints (e.g. /media/music, /media/sdb1, etc).

---

### Post by thavid on 2008-11-06
Or give each partition a logic name. You'll have to do that under Windows (just rename the drive's name), and then, linux will mount it according to it's name (if the name is empty, it will use the label "disk")

---

### Post by canam101 on 2008-11-07
> **drs305 said:**
> Yes, you can put them in fstab, if they are not there already, and identify them by either UUIDs or labels.

If you need help with this, post the results of:
```

sudo blkid
cat /etc/fstab
mount

```


Thanks for the tip. I did the blkid command and got the uids of the three partitions. Looking at /etc/fstab, it looked like I might get away with entering uid, mount point, and file format.

So I did that and rebooted. The three partitions retained their mount point names over several reboots. However, one of them could not be written to. It was vfat, while the others were ext3.
Maybe I just got the name wrong and should have put fat32, I don't know.

After more screwing around with fstab, I ended up with no external disks mounted, even if I restored fstab to what it was at the start. The linux mount system looks kind of unforgiving.

Luckily, I had a backup of the system, and when it was restored, the disks appeared agagin.

Then I got into gparted and re-formatted the vfat drive as ext3.

I got the new uid for it and changed fstab again.

This time when I rebooted, all disks were present and writeable, and the mount point names will stay the same I hope.

---

### Post by drs305 on 2008-11-07
canam101,

congratulations for getting it figured out for yourself. If you now have the entries in fstab and they are mounting correctly, the mount points won't change. As you discovered, if you reformat a partition the uuid's change and you would have to update fstab.

If you don't have any other questions on this issue, please mark it solved via the 'Thread Tools' link at the top right of the first post. You can also mark it 'unsolved' via the same link ;-)

Welcome to the ubuntu forums!

---

### Post by LowSky on 2008-11-07
> **thavid said:**
> Or give each partition a logic name. You'll have to do that under Windows (just rename the drive's name), and then, linux will mount it according to it's name (if the name is empty, it will use the label "disk")

I'm pretty Sure Gparted can also be name partitions. I think I did that when I installed Ubuntu the last time

---

### Post by canam101 on 2008-11-07
Thanks again. I have marked it 'solved'. If I knew how to do the electronic 'thank you' I would, but my typed in version will have to stand alone.

---

