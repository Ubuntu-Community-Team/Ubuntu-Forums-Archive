---
title: "Copying files from ext4 to NTFS"
date: 2016-04-16
forum: New to Ubuntu
---

### Post by ron177 on 2016-04-16
Hi all,

I am trying to copy a few files from an Ubuntu-based (ext4) external drive I have to my NTFS external drive. I opened up ext4 hard drive in Windows (it's read only) and started copy / pasting to NTFS. Two or three folders have been transferred but not all. It doesn't give me any error message or any signs to figure out what's going on. Why some files and folders are copy pasted and some not? 

By the way, does this kind of transfer corrupt the files or folders by any chance? I have mostly mp3 and doc files. 

Thanks a million.

---

### Post by papibe on 2016-04-16
Hi ron177.

Usually vanilla Windows is not able to read ext4. What are you using to read it under Windows?

There are characters used in file and folder names that are invalid in NTFS under Windows. However, since the NTFS Linux driver is more flexible, I'd recommend mounting the NTFS drive under Linux, and copy the the files from there.

Another good side effect of doing in this way is that you can use a (verbose) command tool to copy the files, so you can see if there's a problem with a file or a folder.

Just some thoughts, hope it helps. Let us know how that goes.
Regards.

---

### Post by ron177 on 2016-04-16
Thanks a lot. This is very helpful. I will go ahead and do just that. I am using a software called EXT2FSD. It allows Windows to open and read ext4 drives. It says that it can allow write in ext 2 as well but not in ext4. 

I will do as you suggested. But one side question: one is the disadvantage of using NTFS in Linux? Why not more people who are using two OS's use NTFS rather than ext4?

---

### Post by papibe on 2016-04-16
> **ron177 said:**
> ... disadvantage of using NTFS in Linux? Why not more people who are using two OS's use NTFS rather than ext4?
Several reasons:
[LIST]
[*]It is a proprietary file system. The linux driver is reverse engineered. Although for personal use may be fine, companies might have legal issues with that.
[*]It does not support permissions, so it would not be possible the level of security that Linux have. For example, it is not even possible to have a Linux root file system on NTFS.
[*]It's old. Latest version (in Windows) is v3.1 from 2001.
[*]Its performance degrades with time. A pristine, empty, recently formated NTFS partition is super fast, but with time it becomes slower than ext4, and others.
[*]
[/LIST]
Regards.

---

### Post by yancek on 2016-04-16
> But one side question: one is the disadvantage of using NTFS in Linux?

Linux won't run on an ntfs filesystem.  The only use of an ntfs partition from Linux is to store data to access from both.  As you have found, a windows default system will not read a Linux filesystem much less write to it.

---

### Post by mastablasta on 2016-04-18
> **papibe said:**
> 
[LIST]
[*]Its performance degrades with time. A pristine, empty, recently formated NTFS partition is super fast, but with time it becomes slower than ext4, and others.
[/LIST]


yes, fragmentation is a lot lower in ext4 than NTFS.

NTFS uses attributes to give permission to files and then it's further set on system level. while linus already gives and takes permisison on file level. it just Works in a different way and NTFS doesn't fit into it. : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Even Ext4 is not the most advanced. ZFS (due to licencing issues not auto-included in Linux) and BTRFS are a lot more advanced than both the EXT4 and NTFS. among other things they offer snapshots of previous disk state, so one can easilly roll back. for example: [https://en.wikipedia.org/wiki/Btrfs](https://en.wikipedia.org/wiki/Btrfs)

NTFS doesn't differentiate between letters. FILE.exe is same as file.EXE or FiLe.ExE
Also with NTFS and Windows ending plays a role. not so much in Linux where it is used to help the user but otherwise doens't have much meaning.

---

