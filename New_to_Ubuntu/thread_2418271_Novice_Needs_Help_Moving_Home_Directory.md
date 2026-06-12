---
title: "Novice Needs Help Moving Home Directory"
date: 2019-05-04
forum: New to Ubuntu
---

### Post by bonzo2 on 2019-05-04
Greetings,

I'm running Ubuntu 16.04 and have been trying for months to move my home directory to a dedicated internal HDD. I must admit I've failed. As a true novice, I cannot even make sense of the instructions I've located. 

Would anyone here be willing to walk me through the steps at an elementary level? I'd like the sort of set up that completely segregates the OS and programs from data so that should I elect to reinstall Ubuntu on the SSD, all of my data, including Thunderbird, desktop, documents, pictures, and etc. would be safe. If possible, I'd like all data to be stored by default on the HDD.

I formatted the HDD as FAT because my understanding is that if I wanted to be able to access data on that drive via all operating systems (not just Ubuntu), FAT would be the best choice. If my understanding about this is incorrect, I'll certainly reformat it.


Dell 5570 laptop
SSD 250 GB 
HDD 2 TB ("D Data" FAT 32)

Thanks for reading. 
Bonzo
.

---

### Post by TheFu on 2019-05-04
You cannot use FAT for HOME directories.  Only a supported, Linux-native, file system can be used.  That means, one that supports userids, groups, permissions, and ACLs.  ext4 is the best choice, lacking to other requirements.

No, you cannot use NTFS either.

Learn and understanding Unix file and directory permissions is critical for your effort to work.  Have you got that down?

I'm terrible at explaining things to beginners, so someone else will need to help. But the overall ideas are really simple.  
As long as the correct files appear to be in the correct directories with the correct owner, group and permissions, that all that matters.  Where any files are physically located is unimportant.  The underlying use of HDD, SSD, doesn't matter, provided the items above are met.

Also, it is common to place many things that usually reside in a HOME somewhere else by using symbolic links.  Lots of people make a link from ~/Documents/ to /some/other/mounted/storage/Documents.  This other storage CAN be NTFS or FAT-whatever.  I suspect you really want to use NTFS for either SSD or HDD storage for many reasons.  FAT, FAT32, exFAT all have limitations that just aren't necessary for any computer where the storage will be directly connected.

Settings need to be on Linux file systems, due to permissions requirements. That applies to Thunderbird as well, I would assume.  However, you can definitely copy the thunderbird settings and files between OSes. They are binary compatible across x86 OSes. I've done this between Windows, Linux, OSX.

Also, if you only need access over a network connection, then using Linux file systems and making that network-shared in the best format for each client is possible.

How you get from what you have today to what you desire has 500 possible choices.

See how I'm terrible at helping new people? Sorry.

The best starting point is to post some data here (not images!!!!!), using "code tags" so it lines up like the commands show in a terminal.  If you don't see the same indentation after posting, try again, by using the Adv Edit.
For now, the main commands needed are:
```

df -Th
lsblk
```
See how it says "code:" just above the block?  Your post needs that too, with the command AND output. The advanced editor has a button.

I assume you've seen this? [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by CatKiller on 2019-05-04
> **bonzo2 said:**
> I formatted the HDD as FAT because my understanding is that if I wanted to be able to access data on that drive via all operating systems (not just Ubuntu), FAT would be the best choice. If my understanding about this is incorrect, I'll certainly reformat it.

As I understand the situation from the way that you've described it, you have Ubuntu installed on an SSD, and you have a separate HDD. You would like your /home separate from your Ubuntu install to preserve your settings in case of reinstall. You would like to be able to access your data from within Windows.

As TheFu says, you can't use FAT for your home folder because it isn't capable of retaining permissions. As you already know, Windows isn't capable of reading ext filesystems natively.

My recommendation for your situation would be to create a small ext4 partition for your /home. For just your settings, it doesn't need to be large. You could make it on either the SSD or the HDD.

Then make a large partition on the HDD and format it with either FAT or NTFS, as you prefer. This will be either the entirety of your HDD or the amount that's left after you've created your /home partition. You'll use this for storing the data that you want access to from other operating systems.

Once you've got both partitions mounted and set up, you can use symlinks so that directories in your home folder for things like documents, music, videos, and so on, actually point to directories on your large partition.

---

### Post by oldfred on 2019-05-04
I consider a separate /home as the first stop beyond a very new user with just / (root). 
And then the next step is separating some data into data partitions. But too many partitions can create issues of size management, so best to have used system for a bit to know how much space you need.

TheFu link on moving /home is a good step by step way to create a new /home.

I keep /home inside /  (root) as I have several installs on one system and at least one install on every drive, including large flash drives.
But each system has only one large data partition which I mount into every install and copy/backup to other systems. I do not want /home as separate partition as I have one main working LTS install, and others are tests and I do not want those settings changing my main install.
Similar posts:
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
[https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) & 
[https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk](https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk)

---

### Post by SeijiSensei on 2019-05-05
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

---

### Post by TheFu on 2019-05-05
> **SeijiSensei said:**
> [https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

That is a good thread.  

I've completely changed my thoughts on LVM since then. For any lurkers coming in a few months, keep reading. If you don't have LVM, don't bother.

On a freshly installed system with a single LV for /, splitting off /home to another LV is really easy, assuming LVM is understood. This is not for the Novice, unless they choose LVM during the base Ubuntu Install.  Another good point is that using full-disk-encryption doesn't make splitting LVM off any harder.
```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                         8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1                      8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                      8:2    0   732M  0 part  /boot 
&#9500;&#9472;sda3                      8:3    0 464.6G  0 part  
&#9474; &#9492;&#9472;sda3_crypt            253:0    0 464.6G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root     253:1    0    25G  0 lvm   /
&#9474;   &#9500;&#9472;ubuntu--vg-home--lv 253:3    0    75G  0 lvm   /home 
&#9474;   &#9500;&#9472;ubuntu--vg-stuff    253:4    0   100G  0 lvm   /stuff
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1   253:2    0   4.5G  0 lvm   [SWAP]
```
That's the setup on my laptop, which uses FDE and LVM.  Initially, ubuntu--vg-home--lv and ubuntu--vg-stuff didn't exist. ubuntu--vg-root was huge - like 450G+.  I always leave unused space for LVM to allocate later. Turns out that leaving 20% of an SSD unused drastically extends the lifespan too.

I don't backup /stuff, /boot or /boot/efi.  My restore methods don't require those areas.
I do backup /, /home, which is why I want them limited in size.  Basically, 100G is important on this 500G SSD.

---

