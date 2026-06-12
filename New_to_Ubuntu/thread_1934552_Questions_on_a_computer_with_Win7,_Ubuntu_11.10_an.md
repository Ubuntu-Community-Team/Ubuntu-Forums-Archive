---
title: "Questions on a computer with Win7, Ubuntu 11.10 and Linux Mint 12"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by hanzj on 2012-03-02
We currently have a laptop with Windows 7 and Linux Mint 11. We plan on installing Ubuntu 11.10 and Linux Mint 12. What is the best way of installing these two linux distros? I'm particularly uncertain of the best way to answer the partition questions that the installation will ask. 

I booted up the "Ubuntu 11 Iso" on my computer. The installer was aware that I had "other operating systems". It asked me whether I wanted to install Ubuntu 11.10 alongside them. I did, and then I was led to "Guided Installation". I saw this screen:

[IMG]http://i.imgur.com/pOanH.jpg[/IMG]

But that worried me. Where were was Linux Mint? And why was Ubuntu going to be installed in sda3? sda3 is Windows Recovery Environment loader (ntfs), according to the "Manual Partition" option. The screen does say that "4 smaller partitions are hidden", but that scared me. So I went and clicked onto Manual Partitioning:

[IMG]http://i.imgur.com/lBFsb.jpg[/IMG]

sda1 ntfs 1.6GB Windows 7
sda2 ntfs 209GB Windows 7
sda5 ext4 93.9GB Linux Mint 11 Katya
sda6 swap (linux-swap) 4.1GB
sda3 ntfs 11.1GB Windows Recovery Environment 

Some questions:
1. Why is Windows 7 split into sda1 and sda2?
2. Do I need sda6 linux-swap?
3. What's the proper way to make room for Ubuntu? What must I click on the screen?

Also, I'd like the 2 distros to share the same "home" folder. By this, I mean that I want both of them to point to the same place for where I save my stuff (same Downloads folder, same Photos folder, same "Recent" stuff, etc)

Some bits of info:
The laptop has only one hard drive.

 all other advice will be appreciated.

---

### Post by seawolf167 on 2012-03-02
[LIST=1]
[*]These are the Recovery partition and OS partition respectively.
[*][SWAP]("https://help.ubuntu.com/community/SwapFaq") is hard drive memory swap space. You most likely don't need 4GB; 2GB should be more than plenty. SWAP can be shared between your two linux distros since they won't be running concurrently.
[*]Here is what I would do...
[/LIST]

Boot into Windows, use the Windows partition editor (right-click "My Computer" select "Disk Management" from the "Storage" category) and use that to resize your Windows install to make room for your linux installs.

Next, I would manually setup the partitions for your linux installs. When booting the install cd, select to partition manually (might be called "advanced" or something). 

Some notes:

[LIST]
[*]Each distro (Ubuntu & Linux Mint) need their own root (/) directory, each should be 10+ GB, but IMO not more than 15-20GB
[*]Setup one swap partition and mount this single partition as type swap for both distros
[*]I suggest that each distro have their own home (/home) partition/folder since this is where all the configuration files are stored, and having conflicting info from two different distros can cause all kinds of headaches
[*]Each distro can access the other's files, so you have a couple options
[LIST]
[*]A separate "data" partition for all your pictures, videos, etc. (needs to be formatted NTFS for windows to be able to access it)
[*]Mount your Pictures, Videos, etc. folders on one of the distros and point to that distro's respective folders
[/LIST]
[*]You can make additional partitions as you see fit for other items such as /boot, etc.
[/LIST]
After you get everything installed, boot into one of the linux distros and run

```
sudo update-grub
``` so that Grub (the MBR) picks up the other installations and gives you menu options at boot.

Backups are always a very good idea when playing around with partitioning, especially when you are unsure what you are doing. I suggesting using [Clonezilla ]("http://ubuntuforums.org/www.clonezilla.org")to make a full disk image before you start.

---

### Post by hanzj on 2012-03-02
> **seawolf167 said:**
> 

Boot into Windows, use the Windows partition editor (right-click "My Computer" select "Disk Management" from the "Storage" category) and use that to resize your Windows install to make room for your linux installs.

Next, I would manually setup the partitions for your linux installs. When booting the install cd, select to partition manually (might be called "advanced" or something). 


Seawolf, thanks for your reply.
Is it necessary to boot into Windows? It seems that the Ubuntu installer can resize the Windows install/partition.

Why can't I both resize  current partitions and create new partitions through the UBuntu installer?

---

### Post by Jerry N on 2012-03-02
> **hanzj said:**
> Seawolf, thanks for your reply.
Is it necessary to boot into Windows? It seems that the Ubuntu installer can resize the Windows install/partition.

Why can't I both resize  current partitions and create new partitions through the UBuntu installer?

Because gparted might damage the Win 7 partition.  The Win 7 tools are easy to use and it will be safer to use them.  Don't let Win 7 create a new partition though.

Jerry

---

### Post by hanzj on 2012-03-02
I've booted Windows 7 and am in "Disk Management". How much shrinking should I do?

Please see image.
[http://ubuntuforums.org/attachment.php?attachmentid=213606&stc=1&d=1330721524](http://ubuntuforums.org/attachment.php?attachmentid=213606&stc=1&d=1330721524)

Shrink C:
Total size before shrink in MB: 199747
Size of available shrink space in MB 46383
Enter the amount of space to shrink in MB: 46383 (what is preset, but I can make the number smaller)
Total size after shrink in MB: 15364

If I leave the "amount of space to shrink" as is (46383), does this mean that the C: drive will have no more space for additional files?
What do you guys recommend?

---

### Post by seawolf167 on 2012-03-02
> **hanzj said:**
> Seawolf, thanks for your reply.
Is it necessary to boot into Windows? It seems that the Ubuntu installer can resize the Windows install/partition.

Why can't I both resize  current partitions and create new partitions through the UBuntu installer?

You *can* use Gparted to resize the Windows partition, however, I *highly* recommend that you do not, and instead use the Windows partition editor to resize it. After that, you can do everything else with Gparted/Linux-based tools.

---

### Post by seawolf167 on 2012-03-02
> **hanzj said:**
> I've booted Windows 7 and am in "Disk Management". How much shrinking should I do?

Lets work backwards:

[LIST]
[*]swap: 2GB
[*]Ubuntu:
[LIST]
[*]/ (root): 10GB
[*]/home (home): 15GB
[/LIST]
 
[*]Linux Mint
[LIST]
[*]/ (root): 10GB
[*]/home (home): 15GB
[/LIST]
 
[*]Total: 52GB
[/LIST]
Of course, adjust the partition sizes accordingly (i.e. if you know you have some large items for Ubuntu, increase that size or vice versa).

Add in any "data" partitions you may want to setup for sharing between Ubuntu, Linux and/or Windows

EDIT: It looks like you don't have 52GB free, so you will either need to add/remove items from Windows to free some more space or adjust the above values to come in less than your 46GB free.

---

### Post by hanzj on 2012-03-02
Why should each root directory be at least 10GB?
Why should each /home directory be about 15GB?

Or, maybe it's better to ask: What are the root and home directories?
Maybe it's helpful to tell you what I plan to store/install/save on Win7, Ubuntu, Mint. The C: drive is 195 GB big, and there's 103 GB free. About 43 GB is for podcasts. 
On my current Mint OS, I don't have much personal files aside from pics from digital camera (about 5 GB). 

In Windows 7, when I look at the "Computer" folder, C: drive has 103GB free of 195GB. 
You said that it seems that I don't have 52GB free. How come Windows can't make use of the 103 GB? Why is Win7 saying that it can only free up 46GB? 

I'm so confused. My mind is struggling to grasp partitions. All I can comprehend at this time is that I have a C: drive (Windows stuff) and that I have a Linux Mint "area".

---

### Post by seawolf167 on 2012-03-02
Some basic info (not comprehensive):

Root, /, stores the necessary kernel, binaries, configuration files, etc. for the OS to run. The home folder /home stores all the user-specific configuration files, settings, documents, etc. Having separate partitions for /home and / is nice because, for example, if you reinstall your OS and have separate /home and / partitions, you can just overwrite / and leave /home untouched which only takes like 5 minutes and all your settings, files, etc. are all safe.

The current recommended minimum for a fresh Ubuntu installation is 10GB. You probably won't use all that, but its a good place to start since you can always resize later.

I set the /home partitions at 15GB simply to try not to eat up all your disk space but still have room enough for some music, videos, documents, what-have-you.

You can access your Windows files through any linux distro, so viewing your podcasts won't be an issue, and if that is the major things that you have stored you are probably safe for now decreasing the size of your home partition.

As for the Windows free space - can you take a screenshot of the Disk Management section while in Windows? That may make it easier.

---

### Post by oldfred on 2012-03-02
NTFS partitions typically need 30% free to work well. Windows starts to slow at 20% free and just about is unusable at 10% free. Of course Ubuntu needs some free space also and actually hides 5% just to be on the save side.

While we often suggest the separate /home, if you are storing all your data in shared data partitions you do not have to have a separate /home and can leave it inside /, but perhaps make / (root) 20GB. My /home is about 1.5GB with 3/4's of that as .wine for Picasa. But I am very aggressive about any hidden folder in /home that has data gets moved into my data partitions. I have Firefox & Thunderbird profiles in my NTFS shared and kmymoney, as well as all the 'normal' data folders in my separate data partition.

Best case is to have one drive for Windows and other drive(s) for Ubuntu and data.

---

### Post by hanzj on 2012-03-03
> **seawolf167 said:**
> 
As for the Windows free space - can you take a screenshot of the Disk Management section while in Windows? That may make it easier.
Thank you again. I took a screenshot. Pls see [http://ubuntuforums.org/attachment.php?attachmentid=213606&stc=1&d=1330721524](http://ubuntuforums.org/attachment.php?attachmentid=213606&stc=1&d=1330721524)

Is that what you were asking for?

---

### Post by seawolf167 on 2012-03-03
Are the ~80, ~3 and ~10 GB partitions at the end of the drive free space or something else? I don't recall you mentioning them, but I may have missed that.

---

### Post by hanzj on 2012-03-03
Hmmm... I don't know what those 87.44 GB, 3.8 GB, 10.31 GB partitions are. Is there a way for me to find out what these partitions are or whether they are free space? How do I figure out whether these partitions are free space or what are its contents?

---

### Post by seawolf167 on 2012-03-03
> **hanzj said:**
> Hmmm... I don't know what those 87.44 GB, 3.8 GB, 10.31 GB partitions are. Is there a way for me to find out what these partitions are or whether they are free space? How do I figure out whether these partitions are free space or what are its contents?

Easiest way (IMO) since it doesn't appear that you have the partitions mounted in Windows (i.e. no drive letter assigned) would be to boot off a Linux-live cd (Linux Mint or Ubuntu) and simply browse the contents to see what it there (you can also try right-clicking and selecting explore or assign it a drive letter and open it). The first partition is the "recovery partition" which the Windows installer makes during install so you should/can leave that one alone.

As a side note - since the Windows partition editor cannot determine the partition type, they could also be Linux partitions (ext3, ext4, swap) created during a previous installation attempt.

---

### Post by hanzj on 2012-03-03
I'm currently booted into Linux. Is there a command that I can run from Terminal that will do all this (list the partitions)?

---

### Post by seawolf167 on 2012-03-03
You can list all partitions with

```
sudo blkid
```You can [mount]("https://help.ubuntu.com/community/Mount") the partitions with

```
sudo mkdir /mnt/mount_name
sudo mount /dev/sdXY /mnt/mount_name
```where you'll need to replace /dev/sdXY with the partition name you want to mount and mount_name with the name you want it mounted as.

If you are not sure what is mounted, you can view your mounts with

```
mount
```Additionally, you can see free space and total sizes with

```
df -h
```You can also do this all by opening Nautilus (i.e. a window), browsing to the place and using right-click context menus

---

### Post by hanzj on 2012-03-03
```
sudo blkid
```
gives:

> /dev/sda1: LABEL="System" UUID="FA64E61B64E5DA81" TYPE="ntfs" 
/dev/sda2: LABEL="TI106049W0B" UUID="1C860BE5860BBE70" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="9ED431F0D431CAF3" TYPE="ntfs" 
/dev/sda5: UUID="0ca475be-1b9e-4775-889b-bd1a65e783f7" TYPE="ext4" 
/dev/sda6: UUID="46bba95b-cb06-4722-a2ba-0bda21505d00" TYPE="swap" 




```
mount
``` gives:
> 
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda2 on /media/TI106049W0B type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /home/hz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hz)



```
df -h
``` gives:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              87G   18G   65G  22% /
none                  1.9G  692K  1.9G   1% /dev
none                  1.9G  1.4M  1.9G   1% /dev/shm
none                  1.9G  380K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda2             196G   91G  105G  47% /media/TI106049W0B
```


For the purpose of our exercise, should I mount any partitions?

---

### Post by seawolf167 on 2012-03-03
> **hanzj said:**
> 
[CODE]Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda5              87G   18G   65G  22% /**


It looks like the previously mentioned partitions are due to an existing linux-based OS you have installed.

Just so we can clarify things: what is your ultimate goal? Is it to keep the current Windows installation, resize said Windows install to create additional free space, wipe the rest of the disk and install Ubuntu 11.10 and Linux Mint 12 in that free space?

If so, do you have any files, documents, etc. on the Linux install that you want to keep? Do you have a spare external hard drive around? Or a [large] flash drive?

---

