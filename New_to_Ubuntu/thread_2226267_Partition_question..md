---
title: "Partition question."
date: 2014-05-26
forum: New to Ubuntu
---

### Post by gordon99 on 2014-05-26
I have successfully installed Ubuntu 14.04 to dual boot with Windows 7. I have one question however.
During the install procedure I was able to make logical partitions for both /root (20 GB) and Swap (3GB) in unallocated partition space I had  taken from Windows 7 partitions. However I also wanted to make an NTFS partition for /home for sharing with Windows. I have about 80 GB still of unallocated space but I was unable to see how to make an NTFS partition during  the Ubuntu installa\tion.
Would anyone care to enlighten me on the procedure to make this unallocated disk space into a NTFS logical partition. Thanks

---

### Post by lotharmat on 2014-05-26
I'm not sure you if you can during installation.

I think you may need to create a shared partition that is NTFS afterwards using Gparted.

---

### Post by TheFu on 2014-05-26
/home cannot be NTFS.  Linux files that need permissions, ownership, groups must be located on Linux-formated file systems.  Only data files should be shared via NTFS.

---

### Post by mastablasta on 2014-05-26
yeah /home shouldn't not be NTFS. it holds user settings. it is better to just create a separate (data) partition (it will appear in file manager). t do that boot from live DVD and eneter Gparted. select the emtpy disk space and create an NTFS partition there.

---

### Post by LastDino on 2014-05-26
You can't have partition formatted in NTFS during installation. Not that it matters, as TheFu pointed out, you need Linux primary partitions in ext4. By the way, in this situation, I would just keep that 80 GB as storage by formatting it to NTFS after completion of installation and wont bother to make separate /home at all.

20GB space for Linux is more than sufficient if you're not going to store large files on this single partition (and you shouldn't). You can directly use that NTFS partition for that purpose.

---

### Post by rewyllys on 2014-05-26
> **gordon99 said:**
> . . . . During the install procedure I was able to make logical partitions for both /root (20 GB) and Swap (3GB) in unallocated partition space I had  taken from Windows 7 partitions. However I also wanted to make an NTFS partition for /home for sharing with Windows. . . .
You are absolutely on the right track in planning to use a separate partition for your /home directory.  Doing so will greatly ease future updates, upgrades, and other possible  changes in your Linux distro.

But as others have already pointed out, your /home partition must be formatted with a native Linux file format; and NTFS is not such a format.  The recommendation to use your extra NTFS space as a distinct /data partition, for files you want to share with Windows, is a good one.

---

### Post by gordon99 on 2014-05-27
Thanks all for pointing out my error in wanting to use /home as an NTFS partition. I thought I was just copying someone who had written that he had done just that and it seemed like a good idea. Clearly it is not possible . I will therefore follow the recommendation to make a /data partition formatted NTFS.

---

### Post by pfeiffep on 2014-05-27
> I will therefore follow the recommendation to make a /data partition formatted NTFS. Once you've made the data partition you might consider making a [soft link]("http://linux.about.com/library/gnome/blgnome6n6l.htm") to the directories in the data partition.

---

