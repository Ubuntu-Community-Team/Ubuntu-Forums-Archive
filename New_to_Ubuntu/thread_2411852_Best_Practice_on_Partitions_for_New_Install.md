---
title: "Best Practice on Partitions for New Install"
date: 2019-02-04
forum: New to Ubuntu
---

### Post by barddzen on 2019-02-04
I have a new install of Ubuntu and have a main drive SSD (256 GB) configured as follows.  I also have a second drive that I setup two partitions: 1 for Timeshift backups and the other for general storage.

My first question is: what best practice on partitions and sizes should I setup?  Is the below model good enough or should I setup something different? What use cases/scenarios would cause me to have different than was I have below?

```
sda                       8:0    0 238.5G  0 disk  
&#9500;&#9472;sda1                    8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                    8:2    0   732M  0 part  /boot
&#9492;&#9472;sda3                    8:3    0 237.3G  0 part  
  &#9492;&#9472;sda3_crypt          253:0    0 237.3G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root   253:1    0 236.3G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 253:2    0   976M  0 lvm   [SWAP]
sdb                       8:16   0   1.8T  0 disk  
&#9500;&#9472;sdb1                    8:17   0 279.4G  0 part  /media/dyutzy/local-backup
&#9492;&#9472;sdb2                    8:18   0   1.6T  0 part  /media/dyutzy/local-storage


```
My other question is: on the "local-storage" partition, what is the thought to use that partition for? For example, should I have / move my home folder there? What would be the benefit of doing that? Should I put something else there? Why?

---

### Post by TheFu on 2019-02-04
The LV vg-root is much too large.  Anything over 25G is too much.
I'd setup /var/ into a LV and /home into an LV.  Sizes for these completely depend on the purpose of the system.  I usually put 200G for /var/ on VM hosts because that is where VM storage goes by default.  I keep /home/ relatively small by not placing any media files there, but I keep documents, email, code projects, and settings there.   5G is a huge amount for a single-user system /home/.

Backups need to be on a physical disk, alone.  Not shared with any other type of files. Backups only.  Where does "local-storage" get backed up? It cannot be on sdb.

Why use LVM and encryption on sda, but not sdb?  As long as you already have the complexity/flexibility of LVM, why not use it fully to make life easier?

BTW, it would be helpful if the lsblk output were wrapped in code-tags.  Hard to read as it is now.

---

### Post by barddzen on 2019-02-04
Thanks for the reply, I just ran the standard Ubuntu install and didn't change anything as far as initial partitions go which is pretty much what you see above.  

Is there some sort of documentation if I were to do a re-install I could set it up as you suggest? Specifically, how to change the partitions during the install wizard so that they are configured as we are discussing? Or can I modify these partitions without breaking what I already have without a complete nuke and pave?

I currently have my Documents sync'd using Synology's Drive from my NAS and it's ~3.5G currently.  I'm a packrat as far as documents go, so I might need a bit more than 5G for /home/ (are you implying this is in yet another partition?)

For Backups (local-backup) I created this solely for TimeShift backups only. I get your point here, but my thought was it's physically separate from the SSD and would only serve as a recovery option in case the SSD gets borked.

And per you questions regarding "local-storage" I have a separate backup process that backups up that partition to my NAS.  Right now, I'm just running some VM's from there using VirtualBox.  But given it's size, I would like to possibly use that partition for my /home/ folder and then back that up to my NAS.

I have everything pretty much backed up and protected from a recovery stand point, I recently moved from MacOS and was able to get everything shifted without much headache, but with Linux there are options from a partition perspective and I'd like to take advantage of those features as much as possible.  I could reinstall and reconfigure and be back up and running in about 30 minutes tops. 

The standard installs are really easy but I wasn't aware or didn't notice and/or had no clue about how to partition things any way other than the standard install.  As I learn more I'd like to get things more aligned with best practices.

```
NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                     7:0    0   324K  1 loop  /snap/lcavassa-iperf/1
loop1                     7:1    0 140.9M  1 loop  /snap/gnome-3-26-1604/70
loop2                     7:2    0 140.7M  1 loop  /snap/gnome-3-26-1604/74
loop3                     7:3    0  14.5M  1 loop  /snap/gnome-logs/45
loop4                     7:4    0  42.1M  1 loop  /snap/gtk-common-themes/701
loop5                     7:5    0   2.3M  1 loop  /snap/gnome-calculator/260
loop6                     7:6    0 174.4M  1 loop  /snap/spotify/31
loop7                     7:7    0   2.3M  1 loop  /snap/gnome-calculator/238
loop8                     7:8    0  34.6M  1 loop  /snap/gtk-common-themes/818
loop9                     7:9    0    13M  1 loop  /snap/gnome-characters/124
loop10                    7:10   0 202.3M  1 loop  /snap/vlc/770
loop11                    7:11   0    91M  1 loop  /snap/core/6350
loop12                    7:12   0  89.5M  1 loop  /snap/core/6130
loop13                    7:13   0  91.1M  1 loop  /snap/core/6259
loop14                    7:14   0    13M  1 loop  /snap/gnome-characters/139
loop15                    7:15   0   3.7M  1 loop  /snap/gnome-system-monitor/57
sda                       8:0    0 238.5G  0 disk  
&#9500;&#9472;sda1                    8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                    8:2    0   732M  0 part  /boot
&#9492;&#9472;sda3                    8:3    0 237.3G  0 part  
  &#9492;&#9472;sda3_crypt          253:0    0 237.3G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root   253:1    0 236.3G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 253:2    0   976M  0 lvm   [SWAP]
sdb                       8:16   0   1.8T  0 disk  
&#9500;&#9472;sdb1                    8:17   0 279.4G  0 part  /media/dyutzy/local-backup
&#9492;&#9472;sdb2                    8:18   0   1.6T  0 part  /media/dyutzy/local-storage
```

One other question, what is the rationale behind using multiple partitions for different aspects of the install? Better performance? Better resilience against corruption? Easier to restore?

---

### Post by oldfred on 2019-02-04
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[URL="http://www.bbcode.org/reference.php"]http://www.bbcode.org/reference.php
[/URL]
If using Quick Reply then manually type code in  [] at the beginning and [/code] at the end.  I typically click on quote tags and then edit to code tags.

---

### Post by Dennis N on 2019-02-05
What you show is what you get with the full disk encryption choice in the installer. One problem here is easily adding a second OS to this LVM volume, which here is entirely filled by Ubuntu. It seems a second OS would then also need a boot partition outside the encrypted volume? Can't use the same one. 

If I were encrypting, I think I would go with an encrypted "container" like truecrypt (but no longer supported) and veracrypt to avoid the separate boot partition. I custom install my LVM setup, to avoid the one LV taking up the entire volume group, as I normally will be adding a couple of additional operating systems. LVM does not require a separate boot partitiion when the LV is unencrypted.

I don't use a separate home partition, but instead a separate data partition and leave home for program and user configration files specific to each OS. I mount the data partition to a subfolder of /mnt and mount that in /etc/fstab. All operating systems can share the contents of the data partition. That's being efficient.

---

### Post by TheFu on 2019-02-05
Ok, I have a little time this morning.  That is good or bad for you, depends on how you take advice. Asking questions is good, but nobody can answer all the questions in a forum like this.  LVM is an intermediate-level admin skill.  Encryption is an intermediate-advanced skill to use properly. There are dangers in using both without a full understanding of the limitations they each add.  I always use LVM on all my physical system deployments because of the flexibility it provides. 

I always fully encrypt all portable devices, period.  Anything that can easily walk off needs to be encrypted.  There are many more security concerns with just partial encryption. People think they are safer than they are.  If all you want is to ensure that a failed disk can be easily send back for warranty service, then encryption at the partition level alone is sufficient.  Whenever encryption is used, 100%, know-you-can-restore data backups is mandatory.  A physical or logical error on encrypted storage means all the data is gone, gone, gone. No "data recovery" tools will work. None.  If you aren't excellent at system-level backups, don't use encryption.

> **barddzen said:**
> Thanks for the reply, I just ran the standard Ubuntu install and didn't change anything as far as initial partitions go which is pretty much what you see above.  
That isn't true.  You did ask for whole disk encryption.  That trivial checkbox changed everything about the setup.  If you aren't too tied to any data on the machine at this point, I'd suggest you spend an hour and do 4 installations each with different choices.  Installs take about 9 min each here, so 1 hour should be generous to complete 4 installs.  Using a VM to quickly try out the diff install options is how I'd do it.

> **barddzen said:**
> Is there some sort of documentation if I were to do a re-install I could set it up as you suggest? Specifically, how to change the partitions during the install wizard so that they are configured as we are discussing? Or can I modify these partitions without breaking what I already have without a complete nuke and pave? 
Yes and yes, but the documentation isn't "type this" - it is "LVM high level stuff" and you have to understand how to use it within the limitations of the Ubuntu installer.
OTOH, with ext4 and LVM, you can shrink LVs, create new LVs, mount LVs anywhere you need them.  There isn't any GUI for this. It is all done using pv*, vg* and lv* commands. There are many guides for using LVM and any intermediate Linux Admin book will have a chapter about it too.  Did you check out the Ubuntu Server Guide? [https://help.ubuntu.com/lts/serverguide/advanced-installation.html.en](https://help.ubuntu.com/lts/serverguide/advanced-installation.html.en)

> **barddzen said:**
> I currently have my Documents sync'd using Synology's Drive from my NAS and it's ~3.5G currently.  I'm a packrat as far as documents go, so I might need a bit more than 5G for /home/ (are you implying this is in yet another partition?) 
LVs, logical volumes, aren't the same as partitions, but after they are setup, they behave the same, if  partitions could be resized (up or down), cloned, striped, mirrored, and moved easily between different storage and even systems.  But LVs require VGs, Volume Groups, which require PVs, Physical Volumes  (sometimes called PEs[physical extents]), which are all part of LVM2.  People leave off the "2", since it has been LVM2 since the early 2000s.  LVM is also a great way to trash your data by making poor choices or mistakes too. Unix will allow you to shoot yourself in the head, if you like.  The system can't tell whether your command are pure stupidity or pure genius.

So, I'd make /home/ - into a 5G LV for current documents/stuff.  Archived "stuff" would do somewhere else.

Partitions/LV setup is all about backup and recovery architecture.  The goal after any failure is to get back to a working system ASAP with the least hassle possible.  That means splitting the most important data out from the data you need once a year and other data than never changes.

Begin by reducing the current root LV size down to 25G or so.  That will free up lots of space to use for other LVs like for /var and /home purposes.  I'd leave some extra storage unallocated, so you can add it to any existing LV in chunks as needed, when needed.  This is a 10 second process to add storage from the VG into an LV and expand the file system into that newly added space.  It all happens while online and using the storage.  Try to do that with partitions (you cannot).

> **barddzen said:**
> For Backups (local-backup) I created this solely for TimeShift backups only. I get your point here, but my thought was it's physically separate from the SSD and would only serve as a recovery option in case the SSD gets borked. 
I know nothing about timeshift, but I'm excellent at backups and disaster recovery.  Backups need to be on separate disks from any other current/live data.  An entire disk fails, not just a partition or LV.

> **barddzen said:**
> And per you questions regarding "local-storage" I have a separate backup process that backups up that partition to my NAS.  Right now, I'm just running some VM's from there using VirtualBox.  But given it's size, I would like to possibly use that partition for my /home/ folder and then back that up to my NAS. 
By having backups in 2 different places, you've doubled the chance of a backup storage failure.  Pick 1 place to hold backups.  Either have a failed primary storage or have failed backup storage. Avoid having both over 1 disk having issues.

> **barddzen said:**
> I have everything pretty much backed up and protected from a recovery stand point, I recently moved from MacOS and was able to get everything shifted without much headache, but with Linux there are options from a partition perspective and I'd like to take advantage of those features as much as possible.  I could reinstall and reconfigure and be back up and running in about 30 minutes tops.  
No need to reinstall. LVM is extremely flexible.

> **barddzen said:**
> The standard installs are really easy but I wasn't aware or didn't notice and/or had no clue about how to partition things any way other than the standard install.  As I learn more I'd like to get things more aligned with best practices. 
"Do something else" is the option.  But if you choose whole disk encryption, it gets really complicated, fast. Paddy has written a guide for doing the non-trivial encrypted setups. Search these forums for that guide.  I think it was updates last fall.

> **barddzen said:**
> 
```

NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0 238.5G  0 disk  
&#9500;&#9472;sda1                    8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                    8:2    0   732M  0 part  /boot
&#9492;&#9472;sda3                    8:3    0 237.3G  0 part  
  &#9492;&#9472;sda3_crypt          253:0    0 237.3G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root   253:1    0 236.3G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 253:2    0   976M  0 lvm   [SWAP]
sdb                       8:16   0   1.8T  0 disk  
&#9500;&#9472;sdb1                    8:17   0 279.4G  0 part  /media/dyutzy/local-backup
&#9492;&#9472;sdb2                    8:18   0   1.6T  0 part  /media/dyutzy/local-storage

```

Snap/loop stuff in the storage output is useless unless you are having snap/loop issues. No need to ever include that data otherwise.

BTW, I'm not a fan of using /media to mount local storage and would only allow a GUI tool/file manager to mount storage needed for temporary reasons, say 5 min or less due to the terrible performance.  For storage that is always connected via SATA or eSATA or infiniband, use the fstab to mount it.
For storage that is sometimes connected like NFS or USB external storage, but where you want the best possible performance, use autofs.  Never assume NFS is always connected, since the other device might be powered down.  Both the autofs and fstab support fine tuning of mount options, which improves performance and avoids the use of gvfs (which is almost always what you want).  OTOH, if a GUI tool mounts the storage, GVFS is almost always used causing a 30+% drop in performance and breaking many applications because it doesn't setup a "real mount" as far as the OS is concerned. Some applications care.

BTW, a **df -hT** would be helpful, with code tags, of course. ;)

Also, the LVM link above has lots of excellent links at the bottom of that page to more LVM docs.  LVM is LVM is LVM across all Linux distributions.  Further, LVM is very, very, very, similar to the storage tools used on all Unix systems, AIX, Solaris, HP-UX, Irix, ... all have volume management tools.  With 3 levels of abstraction, the flexibility is awesome.  Pretty much anything you can imagine is possible.  But in the normal Unix way, it is up to the admin not to do stupid things. The tools will allow you to shoot off a finger, foot, leg, or head. It is up to you to choose the right path.  Some more links:
[https://access.redhat.com/solutions/269953](https://access.redhat.com/solutions/269953)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

Common lvm commands:  lvdisplay, vgdisplay, pvdisplay, vgchange, lvresize, pvcreate and to quickly gather information in concise format, I use lvs, vgs, pvs.  All of these require sudo.

I would caution against spanning VGs/LVs across different physical disks, unless they are all enterprise grade SSDs. I lost a bunch of data long ago by spanning 3 disks into a single file system.  This was before I had backup religion.  1 disk failed. All the data on the other 2 drives became unavailable.  I shot myself in the leg when that happened.

This advice is all meant to help you avoid mistakes that I've made looking back over 20 yrs as an admin, trainer and technical architect.

Completely switching gears ... any way I could get you do switch away from Virtualbox for KVM+libvirt?  ;)  Better stability, better performance, better remote management of any interest?  There are good reasons to stay with vbox too.  But, whatever you do, only have 1 hypervisor installed on the system at a time.

---

### Post by barddzen on 2019-02-05
Dennis: Thanks for the reply and info.  This is my first foray into Linux in over 15 years and getting back into it has been a really great experience, but it has highlighted a lot that I've forgotten.  This meant that I really didn't know much in how I should/shouldn't do the lower level setup like partitioning.  I played around with various distros for about 6 weeks and settled on either Mint or Ubuntu as a first leap.  I have Mint on a few older laptops in the house and Ubuntu on my main machine.

My use of Synology's Drive is what I've been using to keep my "Documents" in sync between different machines and partitions and VM via my NAS.  Other than this, I have some apps installed and have been figuring out 1:1 equivalents between MacOS and Linux.

I'm still trying to figure out how to auto mount and have been reading up on fstab, but I haven't got the courage up yet to edit it ;)

---

### Post by barddzen on 2019-02-05
Thank you for all this detailed information!  I've copied it and will need some time to sift through and digest it all, so don't take my lack of response as anything more than I'm taking what you've said and working on it.

---

### Post by barddzen on 2019-02-05
Ok... I also had a bit of time today and started playing around with the partitions on a new install. It got a bit hairy but a little more research and here is where I ended up:

[B]ASSUMPTIONS:
[/B]- I'm not encrypting anything, this is a laptop but I don't plan on taking it with me anywhere, I have it in a docking station on my desk in my house.

**FIRST VM (75 GB VDD)**
sda
- sda1 25 GB part /
- sda3 48 GB /home
- sda5 4 GB part [SWAP]

The thought here was that I would allocate 4GB RAM = the amount I allocated to the VM (I have 16 on the host machine) to SWAP, 25 GB to boot and the rest to home.  Now in this instance I created everything as a primary partition.

The VM booted, everything is fine.  

**CONCLUSION: **I will have ZERO options later if I want to re-partition or resize because everything was allocated as primary.

[B]SECOND VM (75 GB VDD)
[/B]sda
- sda1 25 GB part /
- sda2 extended
   - sda5 4GB SWAP 
   - sda6 15 GB /home

unallocated 36430 MB

In this case, I created /home as a logical partition and the rest as primary and left the rest as free.

**CONCLUSION: B**ased on what you said earlier, is I'll be able to allocate the free space later as needs expand or I want to dual boot or something else...

**OTHER INFO**
Since this was an SDD, I didn't create a /boot partition and just went with /.  From what I've read, if this was a spinning disk, I would want to create a /boot partition first to make sure it's located properly on the disk for optimal speed, then I would also create a / as I did above.  But with SSD, I didn't really need to do that (assumption).

One other aspect here, if I was to do this on the *actual* system (vs a VM), from what Ubuntu did on the default install, it created the following:

NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0 238.5G  0 disk  
&#9500;&#9472;sda1                    8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                    8:2    0   732M  0 part  /boot

Would I still need to create the /boot/efi and /boot partitions or could I also get away with just doing / (as root)?

One last question:  is it normal to leave so much unallocated space?  This seems odd to me coming from other operating systems where everything is typically allocated for app installs and documents and other media (videos, music) etc.  

What also seems odd is allocated such a small amount to / (root) where app installs (again, my experience in other OS) takes up the vast majority of the drive.  Hell installing some games and productivity suites takes up more than 25GB. Is this just the nature of Linux apps in that they don't take up as much space?

Does this all sound like I'm on the right track?

---

### Post by oldfred on 2019-02-05
Do not confuse /boot and an ESP - efi system partition which does have the initial boot files for UEFI boot in it. The ESP is more equivalent to the MBR in the boot process.

Even with hard drives, there is little reason for a separate /boot partition with most desktop installs. But some server or server type installs and full drive encryption do usually use a /boot partition.

Not sure of logic used for default installs, but think still based on dual boot or much older hard drives. So default install just has / (root). It used to have / & swap but they have changed to use a swap file. But if you do have a swap partition that will be used. And just / keeps it simple for newer users.
And if UEFI, it will create or use an ESP, FAT32 with boot flag.

But once you know a bit about partitions, many want to separate system from data. I used to do that back with Windows, but newer Windows made that difficult. So you can install with a separate /home partition for both your user settings (mostly hidden) and your user data. Some like to have separate data partitions and may or may not have /home as a separate partition.

I have multiple installs and create a shared data partition which I mount in every install. Then I have same files, but not necessarily same user settings, so I can experiment without changing my main working install.

---

### Post by barddzen on 2019-02-06
My goal is to use this for my main, desktop machine.  I don't really plan to have dual boot scenarios at this point.  I'm satisfied running a VM for whatever I'd like to play around with.  I have an i7, quad core, 16GB RAM, SSD boot drive machine that gives me plenty of room to play.  I currently have Ubuntu installed (as I noted above) but have learned enough now to realize that maybe I should have done something different (partitions viewpoint) and more importantly "why" I should change it before I get too far down the road with installs, configuration, and setup.

Again, I appreciate everyone's feedback here, it's helped tremendously.

---

