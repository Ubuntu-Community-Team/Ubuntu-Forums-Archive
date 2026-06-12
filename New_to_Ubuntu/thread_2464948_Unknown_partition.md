---
title: "Unknown partition"
date: 2021-07-16
forum: New to Ubuntu
---

### Post by siralocse on 2021-07-16
Hello, everyone, hope you're fine. 

I've been using Ubuntu since  two or three weeks and everything went well. However, last night I was  exploring the preinstalled apps and when I opened the disks I saw an  unknown partition: 

Block Device
1.0 GB
/dev/vgubuntu/swap_1
855c405a-c7d9-472f-adfe-24370aa30ee3
Ext4 (version 1.0)

Is this normal or should I worry? 

Thank you in advance for your time.

---

### Post by rsteinmetz70112 on 2021-07-17
Not sure what is going on but the name seems to suggest you have installed using LVM and that resulted in a swap partition, or file but a swap partition shouldn't be ext4.

How did you come to see this unknown partition?

 Can you open a terminal window (control-alt-t ) and run the command  swapon and copy and past the results in a reply?

---

### Post by mikewhatever on 2021-07-17
It doesn't look like the partition is unknown. It is identified as a swap partition, which is usually created by default. 
Not sure why the filesystem is ext4, but other then that..., more info would be required.

---

### Post by grahammechanical on 2021-07-17
Please open the Disks utility and take a screenshot of what it shows you and attach it to a post in this thread using the insert image icon.

Regards

---

### Post by TheFu on 2021-07-17
a) When using LVM, a "partition" probably isn't being used for swap.  That looks like an LV - Logical Volume.  
b) Using LVM is great, but very different from anything you've probably seen on Windows or OSX. LVM is an enterprise level storage volume management solution. It is very handy and brings some amazing capabilities. Many long-time users of Linux know nothing about LVM and don't use it because it can be very complex.  But is doesn't need to be complex.
c) An LV can almost always be through about like a partition in the old way, but with many more capabilities.  Resizing an LV on a running system is possible and easy.  Takes about 5 seconds, provided the PV and VG are not fully used.  Those are other LVM objects to help with more complex management.  
If you can run this command:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
and post the command AND the output using 'code-tags', then we'll know much more about your setup. The code-tags part is extremely important so the columns line up correctly.  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code-tag use.

Gnome-Disks is a fairly dumb tool and very little use for LVM systems.

---

### Post by siralocse on 2021-07-19
> **grahammechanical said:**
> Please open the Disks utility and take a screenshot of what it shows you and attach it to a post in this thread using the insert image icon.

Regards

[IMG]https://i.ibb.co/Tw17kDR/screen.png[/IMG]

---

### Post by siralocse on 2021-07-19
> **TheFu said:**
> a) When using LVM, a "partition" probably isn't being used for swap.  That looks like an LV - Logical Volume.  
b) Using LVM is great, but very different from anything you've probably seen on Windows or OSX. LVM is an enterprise level storage volume management solution. It is very handy and brings some amazing capabilities. Many long-time users of Linux know nothing about LVM and don't use it because it can be very complex.  But is doesn't need to be complex.
c) An LV can almost always be through about like a partition in the old way, but with many more capabilities.  Resizing an LV on a running system is possible and easy.  Takes about 5 seconds, provided the PV and VG are not fully used.  Those are other LVM objects to help with more complex management.  
If you can run this command:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
and post the command AND the output using 'code-tags', then we'll know much more about your setup. The code-tags part is extremely important so the columns line up correctly.  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code-tag use.

Gnome-Disks is a fairly dumb tool and very little use for LVM systems.

```
d@D-System:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                    SIZE TYPE  FSTYPE      MOUNTPOINT
sda                   465.8G disk              
&#9500;&#9472;sda1                  512M part  vfat        /boot/efi
&#9500;&#9472;sda2                  732M part  ext4        /boot
&#9492;&#9472;sda3                464.6G part  crypto_LUKS 
  &#9492;&#9472;sda3_crypt        464.5G crypt LVM2_member 
    &#9500;&#9472;vgubuntu-root   463.6G lvm   ext4        /
    &#9492;&#9472;vgubuntu-swap_1   980M lvm   ext4        
sdb                   223.6G disk
```

---

### Post by TheFu on 2021-07-19
So, vgubuntu-swap_1 is the swap (virtual memory) on your system.  It is inside the encrypted LUKS container that you selected during installation.

vgubuntu-root is huge.  Much too large for what anyone would ever need.  

If it was me, I'd boot from installation media, manually use cryptsetup to open the sda3_crypt "LUKS container", then use **vgchange -ay** to get the LVM2 objects seen, then use **lvreduce -r** to reduce the size of vgubuntu-root to something about 40G in size, which is still too large for /, but should fit any needs for at least 3 yrs.  

Then I'd delete the vgubuntu-swap_1 LV, recreate a new swap LV sized at 4.1GB.  That would use these commands: swapoff, lvremove, lvcreate, mkswap, then modify the /etc/fstab for the new name/location of the new swap.  For a desktop, swap should be just a tad over 4GB.  You cannot hibernate, but you can still standby.  For a server, I'd probably leave the swap alone until you 100% know the workload, then ensure that no swap is actually needed and remove it completely.

Then I'd create a "home" LV, probably sized to be 30-50GB (smaller is better), put an ext4 file system onto it and mount it on /home; moving any files/directories in the old /home/ to the new /home in the process.  Because you are in the "Try Ubuntu" environment, the old and new "home" will be mounted to temporary locations anyways.

Because you chose encryption, you got LVM for free.  LVM is an enterprise volume management solution which is designed to be modified while the system is running, but there are limitations.  Resizing an LV to larger size on a running system is easy.  Reducing the size is a little harder and all the used storage is at risk, since Linux/Unix will allow you to resize smaller than the current files require.  Don't do that. It will be bad.

It should do without saying, but make a backup of anything you can't lose BEFORE starting all of this.  During installation, I truly wish that setting up encryption and LVM were easier with custom sizes.  I can't believe that Canonical's install team does what they did here with the sizing.  Anything for root over 50G is just abuse.  They seem to be trying to avoid support calls as the primary goal, not do what's best-practice for storage.

Of course, you can leave this as is.  I think the swap size is too small for a desktop and that the root LV is 10x too large and removes some of the main reasons why people use LVM.  In this LV setup, we cannot use LVM snapshots, for example.  There isn't any room left over for snapshots.  I understand that new users would expect to see their entire HDD available for use after an install, but that isn't normally how Linux/Unix systems work. The price it too high with they default LV setup.

---

### Post by siralocse on 2021-07-21
> **TheFu said:**
> So, vgubuntu-swap_1 is the swap (virtual memory) on your system.  It is inside the encrypted LUKS container that you selected during installation.

vgubuntu-root is huge.  Much too large for what anyone would ever need.  

If it was me, I'd boot from installation media, manually use cryptsetup to open the sda3_crypt "LUKS container", then use **vgchange -ay** to get the LVM2 objects seen, then use **lvreduce -r** to reduce the size of vgubuntu-root to something about 40G in size, which is still too large for /, but should fit any needs for at least 3 yrs.  

Then I'd delete the vgubuntu-swap_1 LV, recreate a new swap LV sized at 4.1GB.  That would use these commands: swapoff, lvremove, lvcreate, mkswap, then modify the /etc/fstab for the new name/location of the new swap.  For a desktop, swap should be just a tad over 4GB.  You cannot hibernate, but you can still standby.  For a server, I'd probably leave the swap alone until you 100% know the workload, then ensure that no swap is actually needed and remove it completely.

Then I'd create a "home" LV, probably sized to be 30-50GB (smaller is better), put an ext4 file system onto it and mount it on /home; moving any files/directories in the old /home/ to the new /home in the process.  Because you are in the "Try Ubuntu" environment, the old and new "home" will be mounted to temporary locations anyways.

Because you chose encryption, you got LVM for free.  LVM is an enterprise volume management solution which is designed to be modified while the system is running, but there are limitations.  Resizing an LV to larger size on a running system is easy.  Reducing the size is a little harder and all the used storage is at risk, since Linux/Unix will allow you to resize smaller than the current files require.  Don't do that. It will be bad.

It should do without saying, but make a backup of anything you can't lose BEFORE starting all of this.  During installation, I truly wish that setting up encryption and LVM were easier with custom sizes.  I can't believe that Canonical's install team does what they did here with the sizing.  Anything for root over 50G is just abuse.  They seem to be trying to avoid support calls as the primary goal, not do what's best-practice for storage.

Of course, you can leave this as is.  I think the swap size is too small for a desktop and that the root LV is 10x too large and removes some of the main reasons why people use LVM.  In this LV setup, we cannot use LVM snapshots, for example.  There isn't any room left over for snapshots.  I understand that new users would expect to see their entire HDD available for use after an install, but that isn't normally how Linux/Unix systems work. The price it too high with they default LV setup.

Thank you very much for explaining so well what's happening with my PC storage. You've really done something very selfless here. 
I thought I was part of that small percentage of Ubuntu users who, somehow, caught some malware or something similar; it's a relief to know that it was a mismanagement of the partitions and nothing more.  

I will put into practice everything you advise. Many thanks again and thanks to the other people as well.

---

### Post by TheFu on 2021-07-21
Partition mismanagement?  Well, not really. 

More like LVM mismanagement.  Of course, what should and could be done is a matter of opinion.

You don't need to touch any partitions or modify the encrypted container or PV or VG on the system.  It is only the LVs that I would touch.  Probably best to work through an LVM tutorial first, since I listed commands, but not all the options.  There is 1 truth.  Whenever resizing an LV, add the **-r** option, so it will resize (up or down) the file system too.  Also, with LVM, the manpages are mandatory reading. Don't try to guess anything.  LVM assumes the administrator knows what they are doing. Ask it to do something stupid and it will, happily.

---

### Post by TheFu on 2021-07-21
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                    SIZE TYPE  FSTYPE      MOUNTPOINT
sda                   465.8G disk              
&#9500;&#9472;sda1                  512M part  vfat        /boot/efi
&#9500;&#9472;sda2                  732M part  ext4        /boot
&#9492;&#9472;sda3                464.6G part  crypto_LUKS 
  &#9492;&#9472;sda3_crypt        464.5G crypt LVM2_member 
    &#9500;&#9472;vgubuntu-root   463.6G lvm   ext4        /
    &#9492;&#9472;vgubuntu-swap_1   980M lvm   ext4        
sdb                   223.6G disk
```

This is like a little picture, but in text.

There are TWO HDD connected.  sda and sdb.  Those device names can change based on the boot and how quickly each is discovered.  Never assume that sda is always sda between boots. ALWAYS CHECK.

sda1 (partition) is the FAT32 (vfat) mandated partition required by UEFI standards. 

sda2 (partition) is the /boot ext4 partition. Any native Linux file system that the UEFI boot code supports can be used for this. Generally, ext2/ext3/ext4 are used. ext2 would be the lightest and since /boot isn't written very often and it is relatively small, the added features provided by ext3 and ext4 (journaled writes) don't really provide much added safety.  /boot is mandatory for LVM and/or encrypted partitions in Ubuntu systems so the initramfs can be outside the more-complex-to-access LVM areas.  Without LVM, /boot doesn't have to be a separate partition.  

/sda3 (partition) is where the LUKS container for encryption is placed. It uses the entire partition, but that isn't actually mandatory. Not using the entire partition doesn't make much sense.  I can't think of any good reason why NOT to encrypt all of sda3. 
Inside that encrypted "container" (sda3_crypt), an LVM-PV has been setup.  This is smart, since the entire sda3 is effectively part of LVM storage management, all encrypted, but can be modified.  Here's an diagram I drew a few weeks ago to help explain: 
[ATTACH=CONFIG]288851[/ATTACH]
Nothing too fancy, but the point is that LVs are inside VGs, and VGs, are inside PVs.  What that diagram doesn't show is that VGs can be made of of any number of PVs from different storage devices and that LVs are also limited only be the available space inside a VGs.  There are liabilities in using PVs on multiple disks, so unless you are going for redundancy, it is best to avoid that and just create a different PV, VG, LV setup for other disks.  But, if you do want to have a RAID1 or RAID10 setup, LVM can do that.  RAID1 can be created post-install.  RAID10 has to be setup on all the disks at the same time. If your RAID skills aren't sufficient to understand why, best NOT to use RAID at all.
Free VG space can be used for snapshots. Snapshots in enterprise tools are handy for many purposes. Generally, before backups, I'll create a snapshot to freeze the blocks to be backed up, mount that snapshot for the backup tool and run the backup on it.  When completed, I remove the snapshot so those storage blocks aren't frozen any more.  
Creating a snapshot before patching would allow returning to that point in time nearly instantly should anything bad happen.  Very handy.  Again, I wouldn't keep that snapshot around too long, just long enough to ensure everything is fine - so a few days typically. Perhaps a week, if you patch weekly.  I wouldn't keep 5 snapshots since it stops those blocks from being freed and holding that much storage could lead to an out of space problem much quicker that expected.

vgubuntu-root is not really the LV name for the root LV.  It is a mash of the VG name and the LV name.  The same applies to vgubuntu-swap_1.
To see how LVM has organized your storage, run these commands:
```
sudo pvs
sudo vgs
sudo lvs
```

To see the different available commands for PVs, enter **pv{tab}{tab}** and the list of commands that start with "pv" will be shown.  That's stuff to look at later, but **pvmove** might be a great time saver, right?  Do the same for vg and lv commands.   Generally, there are **create**, **remove**, **change**, **resize**, and **display** commands.  vg and lv have **extent**, **reduce**, and **rename** commands.   Out of storage and need to add more quickly?  vgsplit could be useful.  I'm not listing all the commands.  Use **apropos lvm** to get a short description of each command.

Anyways, this is about 20% of what LVM supports.  You can thin-provision storage areas of you like.  It can get complex quickly, but in the default Ubuntu setup, it really isn't too complex. We gain most of the LVM power without too many negatives, but we don't need to deal with the more complex capabilities unless we are ready for those.  By just having LVM on a system, under the file systems, we gain much flexibility.

---

### Post by siralocse on 2021-07-21
Okay, I understand better now. Thanks again. I will get to work in this the next few days.

---

### Post by rsteinmetz70112 on 2021-07-22
I've been following this discussion but didn't want to interject myself into it since The FU was doing his usually great job of explaining things.
I do have a few questions about what you're trying to accomplish.

First what is the intended use for the second hard drive /dev/sdb? It doesn't appear to be formatted.

Second is vgubuntu-swap_1 actually used as swap? You can check that by running the command below:
```
$ swapon
```
It will list any currently available swap. An LV can be formatted as swap and lsblk will list it swapon will show it as a partition even though it really isn't. This LV is formatted as ext4 and may contain a swap file. swapon will list it if it's active, but I don't think a swap file can be active on it since it doesn't appear to be mounted. swap is not technically necessary and the amount of swap that's recommended varies depending on who you ask. I generally set swap equal to RAM, others think that that is too much, and recommend 50% of RAM, but drives are cheap and big these days. Back in the olden days the usual recommendation was 200% of RAM almost nobody does that today. Ideally if you have enough RAM you won't use any swap.

Finally you can check /etc/fstab and see if vgubuntu-swap_1 is listed in it.

Enough of my digression.

In any event good luck.

-- 
Rob

---

### Post by TheFu on 2021-07-22
swap doesn't get "mounted". It does need an entry in the fstab.  **swapon -s** and **free -h** will show active swap.
```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       4300796 47308   -2

$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       1.2Gi       256Mi       8.0Mi       2.4Gi       2.4Gi
Swap:         4.1Gi        46Mi       4.1Gi
```

There was a long discussion about swap about 13-15 months ago in these forums. Lots of different opinions provided. If there is interest, go read that.

There are so many old swap sizing recommendations that were used when our systems had 32MB of RAM and a HDD of 1GB was huge.  Those days are gone but those swap size recommendations just won't die.  There are lots of old recommendations for many Linux/Unix things that get carried forward - I certainly do some things the *old way* too.  The trick is to know why the old rules of thumb existed and when they don't make sense anymore.

---

### Post by rsteinmetz70112 on 2021-07-22
If you use a swap file the device it is in I think does need to be on a mounted filesystem.

---

### Post by TheFu on 2021-07-22
> **rsteinmetz70112 said:**
> If you use a swap file the device it is in I think does need to be on a mounted filesystem.

Definitely.  LVs are more like swap partitions, however.
I've never used a swap file on Linux or Unix.  Just seems like a terrible idea.  Just because MSFT does something, that doesn't mean it is a good idea. Sure, a swap file can be an option on a system that doesn't use GPT and already has 3 partitions abused by Windows, but using LVM makes the mandated need for fewer partition moot.

Using GPT removes the need for swap files. Effectively no real limitation on the number of partitions possible.
Using LVM removes the need for swap files. Effectively no real limitation on the number of LVs possible.

---

### Post by siralocse on 2021-07-23
> **rsteinmetz70112 said:**
> I've been following this discussion but didn't want to interject myself into it since The FU was doing his usually great job of explaining things.
I do have a few questions about what you're trying to accomplish.

First what is the intended use for the second hard drive /dev/sdb? It doesn't appear to be formatted.

Both drives are ssd, I don't know if this matters. 
Originally I was thinking to install Windows in that second drive, but now I think it won't happen. So, at the moment, those 240 GB are free.

---

