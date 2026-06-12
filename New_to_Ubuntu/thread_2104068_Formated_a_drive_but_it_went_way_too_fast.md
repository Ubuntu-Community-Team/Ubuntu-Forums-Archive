---
title: "Formated a drive but it went way too fast"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by starstreams on 2013-01-12
I'm not sure what to make of this. In windows I always choose to do a long/slow format so windows can mark bad sectors on the drive. I never format with the quick option.
The other day I added a data drive and formatted it, half as NTFS for my Win7 multi boot and the other half as EXT4 for Linux. But the format only took 2 seconds on the EXT4 section of the drive. That same amount of space on the NTFS volume (same drive) in windows took 30+ mins.
Are slow formats not required for EXT4? I didn't see an option in the disk manager under Linux to choose slow or quick formats. Can't this be done from within the GUI in the disk manager? Or is it required to use the command shell to preform a format that marks bad sectors as it formats?

---

### Post by Wim Sturkenboom on 2013-01-12
What was the command that you used?

I used this a while ago (for ext3)
```

mkfs.ext3 -c /dev/sdb1

```
The -c option specifies the check for bad blocks. On a 1TB disk, it took two to three hours.

From the manpage:
```

       -c     Check the device for bad blocks before creating the file system.
              If this option is specified twice, then a slower read-write test
              is used instead of a fast read-only test.

```

Note: replace sdb1 by whatever applies to your system.

---

### Post by starstreams on 2013-01-12
I didn't use a command as mentioned above.
I wanted to know if this could be done with the Disk manager? And being that the disk manager has an option to format the drive, why would it "default" to a quick format only? ( seems dangerous to me). Whats the point in a disk manger If users have to go the command line to do a simple task like that.

I appreciate this tip Wim Sturkenboom, I'll use that if needed. 
Since this is the second half of the drive I need to format as the first half is formatted as NTFS, I'm guessing I need to enter: 
```
mkfs.ext4 -c /dev/sdb2
```I'd still like to know why the disk manger can't do a long format?

---

### Post by kurt18947 on 2013-01-12
> **starstreams said:**
> I didn't use a command as mentioned above.
I wanted to know if this could be done with the Disk manager? And being that the disk manager has an option to format the drive, why would it "default" to a quick format only? ( seems dangerous to me). Whats the point in a disk manger If users have to go the command line to do a simple task like that.

I appreciate this tip Wim Sturkenboom, I'll use that if needed. 
Since this is the second half of the drive I need to format as the first half is formatted as NTFS, I'm guessing I need to enter: 
```
mkfs.ext4 -c /dev/sdb2
```I'd still like to know why the disk manger can't do a long format?

My Win7 defaults to quick format, just like Disk Manager.  I didn't know about the more thorough disk prep.  Thanks Wim Sturkenboom.  One tip - Disk manager & gparted can create NTFS partitions.  My experience is that Win7 won't recognize the resulting partition, Win7 will need to do its own format.

---

### Post by 3rdalbum on 2013-01-12
I'm not sure what the point is of using 30 minutes each time you want to format the drive.

Modern hard disks are capable of determining bad blocks on their own. If they go to write data to a block and find that the block is bad, they automatically flag it and write the data to a better block. All disks have a hundred spare blocks for this purpose.

Checking every single sector of the disk manually sounds like a waste of time if you're formatting the disk.

If you're worried about bad blocks on a disk, check out its SMART statistics; Disk Utility can read the SMART information from a hard disk and find out how many bad blocks have been flagged. If it starts getting up toward the number of spare blocks, you need to take your data off the disk and drop the disk into the nearest rubbish bin.

A format-and-check-bad-blocks may be useful in some circumstances, especially with old disks, which is why it's possible. The threat of featuritis prevents it from being an option in a GUI. The fact that nobody has time to wait forever for a hard disk to reformat, prevents the option from being the default.

---

### Post by starstreams on 2013-01-12
> **kurt18947 said:**
> One tip - Disk manager & gparted can create NTFS partitions.  My experience is that Win7 won't recognize the resulting partition, Win7 will need to do its own format.
Good to know kurt, thanks
I acctuly created the NTFS volume and formatted that in while in Win7, and did the EXT4 in Lubuntu. 

> **3rdalbum said:**
> 
Modern hard disks are capable of determining bad blocks on their own.

A format-and-check-bad-blocks may be useful in some circumstances,  especially with old disks, which is why it's possible. .

I didn't know that 3rdalbum, Interesting. 
Thanks for this info.

I wasn't sure last night before I read your response and ended up just doing a 
[COLOR=Blue]mkfs.ext4 -c /dev/sdb2[/COLOR] which took about 38mins. The only thing is, I just have to figure out why it's denying permission to write to it even though it's mounted.
I'll Google this one, I can't understand the man/help pages half the time. Even after all the reading I've done on man pages, it must have not been enough. I understand the basic formatting options and how choices are defined. But it never fails.  it seems like every man page I come across will say something that just throws me for a loop. Speaking of that, I didn't even see the -c flag in the man *or* help page for mkfs. But I know it's an option and used it lastnight.


Anyway, thanks to all of you for your input ...*3rdalbum*, *Wim Sturkenboom*, and *kurt18947*.

---

