---
title: "Which file structure?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by sakid on 2008-05-28
Hi everyone,

I wish to configure my computer with an 80gb hdd to dual boot xp and ubuntu. I want to have a shared partition that are accessable by both OS's to put my home directory and my documents.

I understand i need NTFS for windows and ext3 for ubuntu but what file structure would be best for the "shared" partition to make it as smooth and seemless as possible.

Cheers

---

### Post by sayakb on 2008-05-28
Make it NTFS or FAT32. Though you can even make it ext3 (and add an [EXT2IFS]("http://www.fs-driver.org/download.html") driver to windows)
Better keep it as NTFS since FAT32 has the 4GB largest file criteria.

---

### Post by kesman on 2008-05-28
You /home -directory should be on a partition that is ext3, and windows won't let you put C:/documents and settings/user/my documents anywhere else than C:, which is usually ntfs, but don't worry, it is fully read/writeable in ubuntu.

---

### Post by sayakb on 2008-05-28
> **kesman said:**
> You /home -directory should be on a partition that is ext3, and windows won't let you put C:/documents and settings/user/my documents anywhere else than C:, which is usually ntfs, but don't worry, it is fully read/writeable in ubuntu.

Sorry, I missed that out. What was I thinking anyway.. :)

---

### Post by kesman on 2008-05-28
> **LinuxIsInnovation said:**
> Sorry, I missed that out. What was I thinking anyway.. :)

Well I'm not sure if he mean just that, but there's the exact answer to the question, maybe he's more specific next time.

---

### Post by sakid on 2008-05-28
Yeh i know you can only put docs and settings on C:, but you can point my documents to anywhere u like so i was just going to point it to the same spot as /home/user/documents

But I didnt realise my home directory had to be on ext3?

---

### Post by kesman on 2008-05-28
Well it doesn't have to, it just usually is. And I don't think it's wise to have them under the exact same location, it would be better if you have your "my documents" from windows mounted under /home/user/windowsdocs or something in linux.

EDIT: got a little lost here, so this is what I mean:

HDA (your hard drive)
**hda1 (windows installation here, also my documents) (NTFS)**
**hda2 (/home -partition here)(EXT3)**
**hda3 (/ -partition, aka root partition)(EXT3**
**hda4 (SWAP-partition)**

[COLOR="Red"]**OR**[/COLOR]

HDA (your primary hard drive)
**hda1 (windows installation here) (NTFS)**
**hda2 (/home -partition here)(EXT3)** (EITHER HERE OR ON THE SECOND HD)
**hda3 (/ -partition, aka root partition)(EXT3**
**hda4 (SWAP-partition)**
HDB (your secondary hard drive)
**HDB1 (windows's my documents here) (NTFS)**
**HDB2 (/home -partition here)(EXT3)**

Now store your stuff, everythin you want, in my documents in windows, and then mount it in /home/username/something, and you can use it in linux too.

---

### Post by sayakb on 2008-05-28
Plus, depends on what you would use primarily. If you use Ubuntu more, make the common partition and ext3 while use the EXT2IFS driver as indicated above. If you use Windows more, make a common NTFS partition since NTFS generally gets messy, fragmented and sometime, Ubuntu might even screw up NTFS (But thats a very rare case -- unfortunately, I myself have been the victim of such rar incidents for about 5-6 times :().

---

### Post by Jaded Misanthrope on 2008-05-28
What I do (and I have not encountered any problems so far) is to follow the plan on [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) and have my HDD partitioned something like this:

[LIST]
[*]Windows Installation (20GB, NTFS)
[*]Ubuntu Installation (10GB, ext3, mounts as /)
[*]Linux Swap Partition (apparently it's good to have one, 2GB and whatever format Linux swap partitions use)
[*]Ubuntu /home and Windows documents and programs (~80GB, ext3)
[/LIST]

Windows can read and write to ext3 partitions fine using the FS-drive program mentioned on the partition planning section of the Psychocats websites.

---

### Post by sayakb on 2008-05-28
The setups seems fine, only that I'm not sure how efficient is the EXT2IFS (the FS-driver) in handling ext3.. It should be fine otherwise.

---

### Post by Joeb454 on 2008-05-28
It handles ext3 just fine. I use it on a couple of my dual booted PC's :)

---

