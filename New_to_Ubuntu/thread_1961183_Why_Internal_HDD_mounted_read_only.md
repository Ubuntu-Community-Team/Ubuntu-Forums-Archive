---
title: "Why Internal HDD mounted read only?"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by AraiBob on 2012-04-18
I have been using Ubuntu for 7 months and something new has come up. My internal hard drives are now being mounted 'read only', and I can't delete files, or any thing I was able to do just a few days ago.

What happened to change the behavior of mounting the drive?

How can I fix this?

---

### Post by AraiBob on 2012-04-18
Support for 3TB Western Digital internal hdd?

---

### Post by SeijiSensei on 2012-04-18
[http://ubuntuforums.org/showpost.php?p=11838980&postcount=21](http://ubuntuforums.org/showpost.php?p=11838980&postcount=21)

---

### Post by mörgæs on 2012-04-19
Please don't double-post.
Merged.

---

### Post by AraiBob on 2012-04-20
My OS drive is ok. I have four hard drives (I had 5 but one of them died and I have not replaced it yet). Two of the drives (the OS and one data drive) are ok. Two of the remaining drives are data only and both are marked as read only. Both are 2TB Western Digital Green drives. 

The drive that failed was a 2TB Western Digital Black drive. Disk Utility says it had bad sectors. It was still formated as NTFS, and I had backups so I tried to format it ext4. The format seemed to be ok, but I could do nothing with the drive. I have returned it to the dealer for a replacement. The warrantee on the WD Black is 5 years and it was well within that range (expire in 2015).

As for Ubuntu, I first tried Edubuntu. I had an issue and asked the question. I was told to contact Edubuntu support (as if I knew where that might be). SO I switched to Ubuntu, just to get an answer. Never got a satisfactory answer to my problem. (How to install a Brother DCP-185C).

Now, I am asking my second question (and third) and hoping for a better result.

I was using Win 7 Ultimate x64, and began to get daily Windows Updates. In the past when I got this set of actions, it was prior to a 'meltdown' in which I had to re-install whatever version of windows I had at the time. As long as I will have to reinstall everything, I decided to try "Linux" once again. I first tried Redhat in 1995 and 1996 and decided it was not 'ready for prime time'. in 2000 I tried Suse and came to the same conclusion. Finally, in 2011 I tried Ubuntu and it was much better.

---

### Post by AraiBob on 2012-04-20
Morgaes. Did you notice the title is different? I did not consciously merge. I thought I was posting a reply to the issue of Ubuntu 12 upgrade.

---

### Post by Janet92 on 2012-04-20
I have been using Ubuntu for 7 months and something new has come up.

---

### Post by d4m1r on 2012-04-20
> **Janet92 said:**
> I have been using Ubuntu for 7 months and something new has come up.

Cool story bro :cool:

---

### Post by AraiBob on 2012-04-20
More details. Most 'help' on this issue expect the internal drives to begin /dev/xxxx. These drives begin /media/xxxx.  I did NOT make these specifications. It was done by Ubuntu, during the initial installation. These internal drives are now marked 'read only'.

I originally installed 10.04 64bit, which was upgraded to 11.10 64bit without incident.

Then a couple of weeks ago I began to have this read-only issue with one of the drives working poorly. Eventually I gave up on that drive and removed it from the system.

---

### Post by AraiBob on 2012-04-25
All,

I found the 'solution' from someone else who was finding all his removable drives (usb drives) also marked read only. All of them were Windows formated, including ntfs.

I also was having that issue, but my complaint was that two of my internal drives was marked read only. Both of them are ntfs. In addition a third drive that was also ntfs format had failed. It is being replaced. So two separate issues,  hmmm.

I do not know why the one drive failed. But I do know what caused the ntfs drives to be marked read only. In my efforts to deal with the failing drive, I downloaded GParted Partition Editor, and added the option "Tools for doing neat things in NTFS Partitions from Linux (ntfsprogs).

It turns out to be that option is the culprit. By removing that option, my 'read only' issue went away.

I do regular backups of my internal drives, but I did one more to ensure I had the latest backups (now that I could write to my backups). I then formated the two ntfs internal drives (WD 2TB Green) to ext4. one by one, then restored the data from my backups.

An exercise I could have done without. When I get my replacement drive, I will also format it ext4. Let's hope ext4 will prevent damage to the drives and the disks will live long past its warantee.

---

