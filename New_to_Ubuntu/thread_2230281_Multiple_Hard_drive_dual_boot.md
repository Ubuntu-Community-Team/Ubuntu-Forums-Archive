---
title: "Multiple Hard drive dual boot?"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by Sirquacksalotus on 2014-06-18
So, I've been playing around with dual-booting Ubuntu and Windows 7. I've got it working to where it's usable, but right now they're totally separate file structures, etc. I've got this idea in my head for how I'd ideally like this to work, but before I go too far I wanted some feedback. Here's what I'd like to set up:

Disk 1: (120Gb SSD) - 20Gb Partition for Ubuntu - 20Gb Ubuntu Swap - 80Gb for Windows 7 system files. 

Disk 2: 1Tb SATA - I'd like this drive to house all of my Documents, music, videos, but to be visible and editable from both OS's. Is that possible? 

Disk 3: 2Tb SATA - This will mostly be a drive for programs, maybe split into 1Tb for Windows program installs and 1Tb for Ubuntu program installs. 

Disk 4: 500gb External Backup - I want to be able to auto-backup my windows and Ubuntu system images to this. Is that possible to do?

---

### Post by TheFu on 2014-06-18
20G is huge for swap.  2G is recommended, unless you hibernate, then the size of physical RAM.

Disk 2 - format this as NTFS. That's the only way - but you will loss file permissions and security.

Disk 3 - NTFS for windows - EXT4 for Linux .... but 1TB is much, much larger than you'll need.  20G is really enough, plus this will need to be mounted under /usr ... so all linux installed programs go there.

Disk 4 - NTFS used for Windows.  EXT4 for Linux.  Pick a modern backup tool, not tar.  fsarchive is good if you want an image (must boot off some other media), but not very efficient for daily, automatic backups.  I don't bother with system images under Linux. There is a thread about that in the Cafe with many different views.

---

### Post by maazmahmood on 2014-06-18
Your swap is a little big. If you have your windows files saved on Disk 2 already. Then when you go on Ubuntu it'll give you an error when trying to mount. But that is a REALLY easy fix. What I have setup is 1 drive for Windows OS, and another drive for Ubuntu OS. Then the rest of the drives are all shared files between the two.

---

### Post by Sirquacksalotus on 2014-06-18
Great, thanks guys! I'll slim my swap space down some for sure.

---

### Post by grahammechanical on 2014-06-18
> [COLOR=#000000]1Tb for Ubuntu program installs.[/COLOR]

That will not happen. You are assuming the Linux works like Windows but it don't. We do not need to direct an installer where to install the programs. All program files in LInux go in directories in the root directory ( / ) and user related configuration files go in folders in the /home folder.

Unless less you are going to install a large number of non-default applications 20 GB for Ubuntu will be fine. You might want to increase that to 25 GB but remember Ubuntu will install in less than 6 GB. And that includes all the default programs such as web browser, office suite and lots of other stuff.

You are better off having a 20 - 25 GB / partition for Ubuntu and a separate /home partition of any size you want. Then if you need to re-install Ubuntu you can do so without loosing any of the user configuration files that are in /home on the /home partition. 

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

Regards.

---

### Post by yancek on 2014-06-18
For your data drive (Disk 2) you would need to format it with a windows filesystem as suggested above and probably best to use ntfs.  A a default installation of windows is not capable of even reading a Linux filesystem much less writing to it.  There is third party software which might work but it will be much easier for you to use ntfs as your Ubuntu will be able to read/write to it.

---

