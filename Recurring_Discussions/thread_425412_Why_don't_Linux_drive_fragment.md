---
title: "Why don't Linux drive fragment?"
date: 2007-04-27
forum: Recurring Discussions
---

### Post by forrestcupp on 2007-04-27
It's only logical for a hard drive to get fragmented.  Here's a simple example:

You put files A, B, and C on your drive.  Then you delete file B leaving a gap on your physical drive.  Then you put file D on your drive.  There are only two possibilities.  Either your computer will put file D after file C, and there will still be a big gap between A and C, or file D can be put in the gap between A and C.  Then the odds are that D isn't exactly the size that B was.  So either there will be a smaller gap there, or if it's too big, the computer will put part of D between A and C and the rest of D at the end.

This is how hard drives get fragmented.  So how can a Linux drive not get fragmented?

---

### Post by jariku on 2007-04-27
Because Linux systems generally use a journaling file system. What this means is that the file system checks first where the file can fit and puts it there instead of just writing the data starting from the first available block in the hard drive.

[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

---

### Post by omns on 2007-04-27
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by psusi on 2007-04-27
Jariku, you completely misunderstand what a journal does.  A journal has nothing to do with fragmentation at all; it is a place where the kernel records what changes it is about to make before it makes them, so that if it crashes in the middle of making those changes, it can finish making them when the volume is next mounted.  Thus you don't get a set of related changes that are only half done, causing inconsistencies in the filesystem.  

As for the original question, you are correct; all filesystems become fragmented, but linux uses good allocation algorithms that minimize fragmentation so it generally doesn't become a problem, unlike windows, which uses what has been known as the worst allocation algorithm for at least 20 years.  

If you really like watching the disk blocks move around you can use the defrag package in the universe repository to defragment ext2/3 partitions that are not currently mounted.  You almost certainly won't be able to tell any difference though, and there is a slight chance it can screw up your disk, so make sure you backup first.

---

### Post by forrestcupp on 2007-04-27
> **GrantG said:**
> [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Thanks.  This website explained a lot to me.  So it's better to have your files scattered all over the hard drive than it is to have them all in one place, but fragmented.  The only problem I see with this method is that it would make it a lot harder to shrink a partition.

---

### Post by koenn on 2007-04-27
Journaling has nothing to do with it. The non-journaling ext2 filesystem also doesn't fragment (much). 
It's in the way space is pre-allocated for files, so that they can grow without having to be split into two (or more) fragments. As for your example : the free space between 2 files, the result of deleting a file, will only be used for files that fit in there. 
The algoritms used for this are apparently very efficient, and fragmentation only occurs when there is only about 5 % of free disk space left. Fragmentation can be higher in directories with lots of writes and ever changing files (/var, /tmp , space for caches such as on a http proxy server) so on servers these are placed on separate drives so that the read/write actions don't affect other drives with 'normal' files.


Linux also uses a read-ahead mechanism to cache files (or fragments thereof, if any) in a buffer so that the processor doesn't have to wait for the disk read head to move to the next fragment. So, if fragmentation should occur, it would still not affect the speed at which data is made available.

[http://en.opensuse.org/SDB:EXT2_Fragmentation](http://en.opensuse.org/SDB:EXT2_Fragmentation)

---

### Post by macogw on 2007-04-27
While that site linked is good (the geekblog one), it's not true that it doesn't fragment at all.  It does once the drive gets full enough not to leave enough space between files for future writes.  Then again, by the time it's that full, you've got more to worry about than fragmentation...like deleting a bunch of stuff...and once you clear off space, unless you manage to clear off space only in one section (good luck), it'll have enough space again not to fragment.  My root partition has some fragmentation because it's rather small and rather full.  I can see it when fsck runs at startup every 30th mount.  It says something about x% non-continuous or something.

---

### Post by forrestcupp on 2007-04-27
> **macogw said:**
> While that site linked is good (the geekblog one), it's not true that it doesn't fragment at all.  It does once the drive gets full enough not to leave enough space between files for future writes.  Then again, by the time it's that full, you've got more to worry about than fragmentation...like deleting a bunch of stuff...and once you clear off space, unless you manage to clear off space only in one section (good luck), it'll have enough space again not to fragment.  My root partition has some fragmentation because it's rather small and rather full.  I can see it when fsck runs at startup every 30th mount.  It says something about x% non-continuous or something.

Actually, that website says that when a drive gets to be more than 80% full, fragmentation may start to occur.

---

### Post by HunterThomson on 2008-07-07
Well I don't know about that 80% stuff. My /boot partition is 18% non-continuous, / patiton is 16% non-continuous, /home 17%... and /boot is 18% full, / is 21% full, /home is 23% full.......... ((the non-continuous "%" are not exact.... from memory... But darn close)) So, maybe it is not doing that grate of a job hu... maybe I need to tweek something or just not care at all? My Box is still way faster then it ever was running Ubuntu.... Vista---well we all know the answer to that one;) The thing that I don't understand is how did the /boot partition get fragmented:confused: I guess it all dosn't matter do to the pre-chaches. I see now why partitoning like everything is a good Idea. That will totally save you from problems caused by fragmentation.

---

### Post by drumsticks on 2008-07-07
When a figure is quoted as the threshold for fragmentation, you need to consider the size of the existing files. Eg, 80% full with 1GB files is different to 80% full with 1MB files.... Take these figures with a pinch of salt.

---

### Post by Masoris on 2008-07-07
> **HunterThomson said:**
> Well I don't know about that 80% stuff. My /boot partition is 18% non-continuous, / patiton is 16% non-continuous, /home 17%... and /boot is 18% full, / is 21% full, /home is 23% full.......... ((the non-continuous "%" are not exact.... from memory... But darn close)) So, maybe it is not doing that grate of a job hu... maybe I need to tweek something or just not care at all? My Box is still way faster then it ever was running Ubuntu.... Vista---well we all know the answer to that one;) The thing that I don't understand is how did the /boot partition get fragmented:confused: I guess it all dosn't matter do to the pre-chaches. I see now why partitoning like everything is a good Idea. That will totally save you from problems caused by fragmentation.
Yes, you are right. My Ubuntu also has more than 10% of non-continuous, but it still fast enough compare with fresh filesystem. It is one of mystery of Linux.

---

### Post by K.Mandla on 2008-07-07
Moved to Recurring Discussions.

---

