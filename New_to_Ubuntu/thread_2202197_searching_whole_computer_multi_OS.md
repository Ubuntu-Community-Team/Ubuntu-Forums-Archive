---
title: "searching whole computer multi OS"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by crip720 on 2014-01-27
Is there a way to do a search on a computer with multi OSs and hard drives. I usually search each OS one by one, which can be time consuming.  Is there a way to do a search from Dash or nautilus on  one OS, and have it also search the other OSs[mounted].  I am using this search for files, documents, etc.  Thank you.  Colin.

---

### Post by monkeybrain20122 on 2014-01-27
Yeah if you mount the other partitions, you can search in Nautilus. If you want to search in dash, after mounting run
sudo updatedb

---

### Post by crip720 on 2014-01-27
Hi, did a quick search for "guide to kde" that is in 13.04 32b partition from 13.04 64b partition.  Did not work, 13.04 is mounted and did the sudo updatedb first.  Dash only show the partition for 13.04 32b, which I would have to search in .  Dash did show quite a few other things[not right one] also.  13.04 32b was near the end of the list.

---

### Post by monkeybrain20122 on 2014-01-27
Ok, I just tested with my multiboot set up. When the other partition is mounted the first time you can search for files in Nautilus only if you navigate to that partition (in my case it would be fedora_home, from there Nautilus does recursive search so it can locate any file in that partition) but once you have open the file you can search for it in the dash next time when the partition is mounted.

---

### Post by Bucky Ball on 2014-01-28
Off-topic but the bad news is that 13.04 is no longer supported, as of yesterday. Might be time upgrade ...

---

### Post by Mark Phelps on 2014-01-28
You're not actually searching the "OSs"; instead, you're searching the filesystems.  So basically, you're mounting each of the "drives" (which are really partitions) and searching the portion of the filesystem contained in each "drive".

---

### Post by crip720 on 2014-01-28
It was a long shot anyway, it is just that I keep forgetting which OS I have the stuff on.  It would be nice to search for something and have the computer tell me where I have it.

---

### Post by Bucky Ball on 2014-01-28
Coincidentally, I have just now posted something that might help you in that regard. Symlinks.

[http://ubuntuforums.org/showthread.php?t=2202216&page=3&p=12913125#post12913125/post=21](http://ubuntuforums.org/showthread.php?t=2202216&page=3&p=12913125#post12913125/post=21)

This way you can have ONE data drive and create symlinks in the /home directories of each install to use the SAME target. No redundant data, no duplication, doesn't matter what OS you're booted into.

Searching the whole computer a long shot? It is quite do-able, as explained. Create mount points for the various partitions, mount them all with 'sudo mount -a' and start searching.

---

