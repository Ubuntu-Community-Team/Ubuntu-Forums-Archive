---
title: "Back Up Data to 12 TB Drive Failed"
date: 2021-10-10
forum: New to Ubuntu
---

### Post by lambquiet on 2021-10-10
Hello

I recently bought a new Seagate Ironwolf drive. I have it on an external mount with its own power connected to a computer running Ubuntu 20.04.

I ran "Disks" and the drive checked OK. I then went into GPARTED and selected Create partition table.

I selected msdos.

I then created a single ext4 partition for the entire drive.

After, I copied a few TBs of data into the drive and all seemed okay. When I went to confirm if the backed up files were intact and could be played, the computer could not open them.

I thought I should just unmount the drive, power down the external mount, and try again.

Once I powered back up, the computer acknowledged that the hdd connected, but that's it.

DISKS SMART test says everything is OK

GPARTED says that the drive is unallocated for 10.91 TB.

I'm not sure what happened...or what I did wrong.

---

### Post by lambquiet on 2021-10-11
After some further testing by copy and pasting smaller batches of files, I notice that the backed up files are intact with no issues. After a few more small batches, I unmount the hdd and power down the device. 

I then power the device back on and Ubuntu does not mount the drive. I see an error saying structure needs cleaning.

So I decide to give MacOS a crack at this - layperson style. I run the disk utility there, reformat the drive in MacOS Extended Journaled, then try to copy a small batch of files on to the drive.

While the job is in progress, MacOS reports that I disconnected the drive and I shouldn't do that. I look to see the device is still on and there's nothing else going on here.

Layperson me is thinking maybe the Vantec NexStar Hard Drive Dock has gone bad and needs to be replaced before I continue.

---

### Post by ActionParsnip on 2021-10-11
Excellent testing but yeah sounds like a duff drive or some power management stuff is kicking in and interrupting the transfer. I'm not familiar with the device in question so can only make guesses like this.

---

### Post by grahammechanical on 2021-10-11
> I ran "Disks" and the drive checked OK. I then went into GPARTED and selected Create partition table. **I selected msdos**.

That is what concerns me. The msdos partition table is the same a Master Boot Record (MBR) partition table and should not be used on drives greater than 2.2TB. Not only that you are limited to 4 primary partitions. That is right  - only four. To have more than four partitions you need to use one of your four primary partitions as an Extended partition and create new Logical partitions inside the Extended partition. Does that sound complicated? Doing it is also completed.

You should be using GPT partitioning. G = GUID = Globally Unique Identifiers. P = Partition. T = Table. Read about it before you class that drive as faulty.

[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

Regards

---

### Post by lambquiet on 2021-10-11
Thanks for the super helpful replies

I tried to write a detailed message here but then Ubuntu forums kept talking about an expired token and my original message is gone so I'll try to be brief.

After turning on the drive again and mounting it to Ubuntu the volume appears to be a 2 TB, fat32. I think after reading the above, that's a sign that the partition table I chose was incorrect.

My challenge now is to figure out how to get Ubuntu to delete the volume, see the drive as a 12 TB drive once more, and start again. I haven't figured that part out yet.

Also, while I appreciate this as a learning experience. I note that there were no notices that perhaps what I was up to incorrect - maybe the user interface type folks here might be interested!

---

### Post by tea for one on 2021-10-11
> **lambquiet said:**
> My challenge now is to figure out how to get Ubuntu to delete the volume, see the drive as a 12 TB drive once more, and start again. I haven't figured that part out yet.

Open gparted > Device > Create Partition Table > Select gpt

This will erase all data and then you can create partitions/partitions.

Please take care to select the correct device.

---

### Post by grahammechanical on 2021-10-11
One more thing. Once the drive is GPT you can create partitions and format them as you need to. Linux is Ext4. Windows NTFS. As you are using this drive as backup you might want partitions compatible with the OS you are backing up from.

Regards

---

### Post by oldfred on 2021-10-11
+1 on tea for one's suggestion.

If you do have some data on drive, you can use gdisk to convert from MBR to gpt. It should preserve data, but backup still recommended for any data you really want to keep.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

With large drives (I consider anything over 16GB large), I like to have an install of Ubuntu (or lightweight/minimal install) on every drive.
So I make first partition an ESP, second a / (root) and one or more data partitions. If you are saving large media files you may want one large partition, but other uses may be better with smaller partitions, for ease of backup.

---

### Post by lambquiet on 2021-10-11
Thank you all very much! I've learned a great deal.

Tips for Anyone Who Comes Across This Situation:

-Have spare cables handy, and perhaps even spare enclosures or docks in case of failure.
-Test out your huge new drives with small batches of files!
-Gradually  increase the size of the batches of files to push duration - in my case  an increase of duration of 5 minutes was all it took to discover the  errors.
-Instructions online tend to advise using "msdos" for  partition table, but assume you won't be making spaces over 2 TB. Plenty  of instructions online do not express assumptions.

I implemented the GPT partition table.

I  can also advise that after a trip to the local electronics store that  either the dock I was using or the USB 3 B to A cable has gone bad.  Either way, I was not going to chance it so I used a brand new enclosure  off the hop. 

I carried out a few tests with smaller batches of  files. Once my drive powers off and back on again, Ubuntu mounts the  drives without issue. 

I'll be taking these tips with me moving forward.

---

### Post by tea for one on 2021-10-11
That's good news.

Assuming that you have reached a satisfactory result, you can mark the thread as solved.
It helps other users with similar problems.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

