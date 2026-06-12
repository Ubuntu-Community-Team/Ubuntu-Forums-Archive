---
title: "Unable to copy Vista drive to external HD using LiveCD"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by 0parority1 on 2012-09-23
Hi all, ):P

I've been having stability issues on my Vista SP2 system for a little while now most likely due to corrupted OS files. It has finally gotten to the point where System Restore can not keep it stable for any period of time so I'm planning to do a reformat/reinstall and want to do a full backup (not clone) of the drive to my external hard drive. I tried doing a straight copy to the external drive in Windows Safe Mode but it didn't seem to want to copy all of the files so I researched and found some articles that said that a LiveCD could be used to accomplish what I wanted to do.

Fast forward to the point where I have LiveCD running and I'm trying to copy the files but it won't copy the folders with the arrows on them. It gives the message "Filesystem does not support symbolic links". My understanding is that the folders with arrows are shortcuts in Windows, and thus symbolic links(?), but I haven't yet found anything that says how to copy these types of folders or any other alternate solutions. Nothing that I came across mentioned anything about having trouble with these types of folders so I'm stumped.

I'm not quite sure which "Filesystem" is being referred to in the error message. I seem to remember running across something that said there were symbolic links in Ubuntu so I'm wondering if the external drive's file system could be the problem. The source drive is NTFS but the destination (external) is FAT32 I believe. I'm worried that that is the problem but wanted to ask for help before I go any further. Please let me know if any more information would be helpful to help me solve this dilemma.

---

### Post by carl4926 on 2012-09-23
Try dd

[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

---

### Post by coffeecat on 2012-09-23
> **0parority1 said:**
> It gives the message "Filesystem does not support symbolic links".

This is the reason:

> **0parority1 said:**
> the destination (external) is FAT32 I believe.

You'd get the same error if you tried to copy files from a Linux filesystem that included symlinks.

Since you want to do a reformat and reinstall, I can't see any need to copy the symlinks anyway. In fact, if you are going to do a re-install, most of what you want to copy is not going to be needed - everything in \Programs Files and in \Windows at least. If I was in your situation I would only be backing up my personal files, knowing that I would need to reinstall every application that I wanted and have to go through the whole updating process again.

Another point about FAT32 is that it has a 4GB file limit. If you have any large files to backup, you'd be better of reformatting your external drive to NTFS, which would be a more robust filesystem than FAT32 anyway. I assume by external hard drive you mean a conventional HD with platters, not a flash drive. Personally I wouldn't use a flash drive for backup if that was the only medium I had backed up to - they are not as long-lived as most hard drives and can fail suddenly.

---

### Post by rTxx on 2012-09-23
I think the problem may be your external HDD being FAT32 and the limits that imposes on file size etc.  Try converting it to NTFS, rather than reformatting it as that should keep any data you already have stored on it.  If you re-format, you'll lose all the existing data.

Try looking at this guide: [http://news.softpedia.com/news/Convert-a-FAT32-Disk-to-NTFS-in-Windows-Vista-51792.shtml](http://news.softpedia.com/news/Convert-a-FAT32-Disk-to-NTFS-in-Windows-Vista-51792.shtml) or search 'convert fat32 to ntfs vista' for alternatives.  It's really easy - I've done it a few times.

---

